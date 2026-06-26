---
layout: default
title: Write New Entry
permalink: /new-post/
---
<div class="wrap" style="padding:2rem 20px;">
  <div style="text-align:center;margin-bottom:2rem;padding-bottom:1.5rem;border-bottom:1px solid var(--border);">
    <h1 style="font-family:'Playfair Display',serif;font-size:28px;">New Chronicle Entry</h1>
    <p style="font-style:italic;color:var(--sepia);font-size:13px;margin-top:6px;">Fill in the form — then download and upload the file to GitHub _posts folder</p>
  </div>
  <div style="background:var(--cream);border:1px solid var(--border);padding:2rem;">
    <div style="margin-bottom:1.5rem;">
      <label style="display:block;font-size:10px;letter-spacing:2.5px;text-transform:uppercase;color:var(--sepia);font-weight:600;margin-bottom:8px;">Post Title</label>
      <input id="f-title" style="width:100%;font-family:'Lora',serif;font-size:14px;color:var(--ink);background:var(--parchment);border:1px solid var(--border);padding:10px 14px;outline:none;" placeholder="e.g. The Fall of Constantinople, 1453" />
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:1rem;margin-bottom:1.5rem;">
      <div>
        <label style="display:block;font-size:10px;letter-spacing:2.5px;text-transform:uppercase;color:var(--sepia);font-weight:600;margin-bottom:8px;">Historical Era</label>
        <select id="f-era" style="width:100%;font-family:'Lora',serif;font-size:14px;color:var(--ink);background:var(--parchment);border:1px solid var(--border);padding:10px 14px;outline:none;">
          <option>Ancient</option><option>Medieval</option><option>Modern</option><option>Contemporary</option>
        </select>
      </div>
      <div>
        <label style="display:block;font-size:10px;letter-spacing:2.5px;text-transform:uppercase;color:var(--sepia);font-weight:600;margin-bottom:8px;">Author Name</label>
        <input id="f-author" style="width:100%;font-family:'Lora',serif;font-size:14px;color:var(--ink);background:var(--parchment);border:1px solid var(--border);padding:10px 14px;outline:none;" placeholder="The Chronicler" />
      </div>
    </div>
    <div style="margin-bottom:1.5rem;">
      <label style="display:block;font-size:10px;letter-spacing:2.5px;text-transform:uppercase;color:var(--sepia);font-weight:600;margin-bottom:8px;">Image URL (optional — use Wikimedia Commons)</label>
      <input id="f-image" style="width:100%;font-family:'Lora',serif;font-size:14px;color:var(--ink);background:var(--parchment);border:1px solid var(--border);padding:10px 14px;outline:none;" placeholder="https://upload.wikimedia.org/..." />
    </div>
    <div style="margin-bottom:1.5rem;">
      <label style="display:block;font-size:10px;letter-spacing:2.5px;text-transform:uppercase;color:var(--sepia);font-weight:600;margin-bottom:8px;">Your Article</label>
      <textarea id="f-body" style="width:100%;font-family:'Lora',serif;font-size:14px;color:var(--ink);background:var(--parchment);border:1px solid var(--border);padding:10px 14px;outline:none;min-height:250px;resize:vertical;line-height:1.8;" placeholder="Begin your chronicle here...&#10;&#10;Use ## for headings, > for quotes"></textarea>
    </div>
    <button onclick="generatePost()" style="font-family:'Lora',serif;font-size:11px;letter-spacing:3px;text-transform:uppercase;background:var(--ink);color:var(--gold);border:none;padding:14px 36px;cursor:pointer;">✦ Generate Post File</button>
  </div>
  <div id="output-wrap" style="display:none;margin-top:2rem;">
    <div style="background:var(--ink);color:var(--gold);font-family:'Playfair Display',serif;font-size:16px;padding:1rem 1.5rem;border-bottom:2px solid var(--gold);">✦ Your post file is ready!</div>
    <div style="background:#1a1a1a;padding:1.5rem;border:1px solid var(--border);">
      <div style="font-size:11px;letter-spacing:2px;text-transform:uppercase;color:var(--sepia);margin-bottom:8px;">Filename: <span id="out-filename" style="color:var(--gold-light);"></span></div>
      <textarea id="out-code" readonly style="width:100%;min-height:300px;background:#111;color:#e8dcc5;font-family:monospace;font-size:12px;border:1px solid var(--border);padding:1rem;resize:vertical;line-height:1.6;"></textarea>
      <div style="display:flex;gap:1rem;margin-top:1rem;flex-wrap:wrap;">
        <button onclick="copyCode()" style="font-family:'Lora',serif;font-size:10px;letter-spacing:2px;text-transform:uppercase;background:var(--gold);color:var(--ink);border:none;padding:10px 20px;cursor:pointer;">📋 Copy Code</button>
        <button onclick="downloadPost()" style="font-family:'Lora',serif;font-size:10px;letter-spacing:2px;text-transform:uppercase;background:var(--red);color:var(--parchment);border:none;padding:10px 20px;cursor:pointer;">⬇ Download File</button>
      </div>
    </div>
    <div style="background:var(--cream);border:1px solid var(--border);border-left:4px solid var(--gold);padding:1.25rem 1.5rem;margin-top:1.5rem;">
      <div style="font-family:'Playfair Display',serif;font-size:16px;font-weight:700;color:var(--ink);margin-bottom:10px;">📌 How to publish:</div>
      <ol style="font-size:13px;color:var(--ink-light);line-height:2;padding-left:1.25rem;">
        <li>Click <strong>Download File</strong> above</li>
        <li>Go to your GitHub repo</li>
        <li>Open the <strong>_posts</strong> folder</li>
        <li>Click <strong>Add file → Upload files</strong></li>
        <li>Upload the downloaded file</li>
        <li>Click <strong>Commit changes</strong></li>
        <li>Your post is live in <strong>1–2 minutes!</strong> ✅</li>
      </ol>
    </div>
  </div>
</div>
<script>
var gFilename='',gContent='';
function generatePost(){
  var title=document.getElementById('f-title').value.trim();
  var era=document.getElementById('f-era').value;
  var author=document.getElementById('f-author').value.trim()||'The Chronicler';
  var image=document.getElementById('f-image').value.trim();
  var body=document.getElementById('f-body').value.trim();
  if(!title||!body){alert('Please fill in the title and article.');return;}
  var d=new Date();
  var ds=d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0')+'-'+String(d.getDate()).padStart(2,'0');
  var slug=title.toLowerCase().replace(/[^a-z0-9]+/g,'-').replace(/^-|-$/g,'').substring(0,50);
  var excerpt=body.replace(/[#>*_]/g,'').substring(0,160).trim()+'...';
  gFilename=ds+'-'+slug+'.md';
  gContent='---\nlayout: post\ntitle: "'+title+'"\nera: '+era+'\nauthor: '+author+'\n'+(image?'image: '+image+'\n':'')+'excerpt: "'+excerpt+'"\n---\n\n'+body;
  document.getElementById('out-filename').textContent=gFilename;
  document.getElementById('out-code').value=gContent;
  document.getElementById('output-wrap').style.display='block';
  document.getElementById('output-wrap').scrollIntoView({behavior:'smooth'});
}
function copyCode(){
  var ta=document.getElementById('out-code');ta.select();document.execCommand('copy');
  alert('Copied! Paste into a new file in your GitHub _posts folder.');
}
function downloadPost(){
  var blob=new Blob([gContent],{type:'text/plain'});
  var a=document.createElement('a');a.href=URL.createObjectURL(blob);a.download=gFilename;a.click();
}
</script>
