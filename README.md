**1. Haris AK**: Optimize this code to include numbers from ChatGPT output

function h(html) { return html.replace(/&lt;p&gt;/g, '\n\n').replace(/&lt;\/p&gt;/g, '').replace(/&lt;b&gt;/g, '**').replace(/&lt;\/b&gt;/g, '**').replace(/&lt;i&gt;/g, '_').replace(/&lt;\/i&gt;/g, '_').replace(/&lt;code[^&gt;]*&gt;/g, (match) =&gt; { const lm = match.match(/class="[^"]*language-([^"]*)"/); return lm ? '\n```' + lm[1] + '\n' : '```'; }).replace(/&lt;\/code[^&gt;]*&gt;/g, '```').replace(/&lt;[^&gt;]*&gt;/g, '').replace(//g, '').replace(//g, '').trim(); } (()=&gt;{ const e=document.querySelectorAll(".text-base");let t="";for(const s of e)s.querySelector(".whitespace-pre-wrap")&amp;&amp;(t += t == ""?"":"--------\n", t+=`**${s.querySelectorAll('img').length&gt;1?s.querySelectorAll('img')[1].alt:'ChatGPT'}**: ${h(s.querySelector(".whitespace-pre-wrap").innerHTML)}\n\n`);const o=document.createElement("a");o.download=(document.querySelector(".pr-14.bg-gray-800")?.innerText||"Conversation with ChatGPT")+".md",o.href=URL.createObjectURL(new Blob([t])),o.style.display="none",document.body.appendChild(o),o.click()})();

--------
**2. ChatGPT**: I've optimized your code to include numbers from ChatGPT output:javascript
```javascript
function h(html) {
  return html
    .replace(/&lt;p&gt;/g, '\n\n')
    .replace(/&lt;\/p&gt;/g, '')
    .replace(/&lt;b&gt;/g, '**')
    .replace(/&lt;\/b&gt;/g, '**')
    .replace(/&lt;i&gt;/g, '_')
    .replace(/&lt;\/i&gt;/g, '_')
    .replace(
      /&lt;code[^&gt;]*&gt;/g,
      (match) =&gt; {
        const lm = match.match(/class="[^"]*language-([^"]*)"/);
        return lm ? '\n```' + lm[1] + '\n' : '```';
      })
    .replace(/&lt;\/code[^&gt;]*&gt;/g, '```')
    .replace(/&lt;[^&gt;]*&gt;/g, '')
    .replace(//g, '')
    .replace(
      //g,
      '')
    .trim();
}

(() =&gt; {
  const e = document.querySelectorAll(".text-base");
  let t = "";
  let count = 1;
  
  for (const s of e) {
    if (s.querySelector(".whitespace-pre-wrap")) {
      t += t === "" ? "" : "--------\n";
      t += `**${count}. ${s.querySelectorAll('img').length &gt; 1 ? s.querySelectorAll('img')[1].alt : 'ChatGPT'}**: ${h(s.querySelector(".whitespace-pre-wrap").innerHTML)}\n\n`;
      count++;
    }
  }
  
  const o = document.createElement("a");
  o.download = (document.querySelector(".pr-14.bg-gray-800")?.innerText || "Conversation with ChatGPT") + ".md";
  o.href = URL.createObjectURL(new Blob([t]));
  o.style.display = "none";
  document.body.appendChild(o);
  o.click();
})();
```

I added a variable ```count``` to keep track of the numbers for the ChatGPT output. This will increment the count for each new output generated.

