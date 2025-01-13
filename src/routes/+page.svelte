<script>
  function growArea(textarea) {
    textarea.style.height = "1rem";
    textarea.style.height = Math.min(textarea.scrollHeight, 200) + "px";
  }

  async function sendMsg(input) {
    console.log(input);
    const chat = document.getElementById("chat");
    const msg = document.createElement("div");
    msg.innerHTML = `
    <div class="bg-base-300 p-4 rounded-lg">
      <p>User:</p>
      ${input}
    </div>
    `;
    chat.append(msg);

    const answer = await getAnswer(input);
    const ans = document.createElement("div");
    ans.innerHTML = `
    <div class="bg-base-300 p-4 rounded-lg">
      <p>Assistant:</p>
      ${answer}
    </div>
    `;
    chat.append(ans);
  }

  async function getAnswer(input) {
    const res = await fetch("http://127.0.0.1:39281/v1/chat/completions", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({
        messages: [
          {
            role: "system",
            content: "Complete the following sentence",
          },
          {
            role: "user",
            content: input,
          },
        ],
        model: "llama3.2:3b-gguf-q4-km",
      }),
    });
    const json = await res.json();

    return json.choices[0].message.content;
  }
</script>

<div
  id="chat"
  class="absolute top-4 left-8 right-8 h-5/6 space-y-4 overflow-auto"
></div>

<div class="absolute bottom-4 w-full px-8">
  <textarea
    class="textarea border-solid border-2 border-gray-700 h-4 max-h-[200px] w-full"
    contenteditable="true"
    oninput={(e) => growArea(e.target)}
  ></textarea>
  <button
    class="btn btn-info absolute top-2 right-12 min-h-8 h-4 w-4"
    onclick={(e) => {
      let textarea = e.target.parentElement.firstChild;
      sendMsg(textarea.value);
      textarea.value = "";
      growArea(textarea);
    }}
  >
    &gt;
  </button>
</div>

