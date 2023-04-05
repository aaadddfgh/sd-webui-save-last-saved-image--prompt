# sd-webui-save-train-prompt
save stable diffusion webui Last saved image prompt while training 
# use
use following code in console to save prompt(English ver) in localStroge
``` javascript
saveInterval = setInterval(
()=>{
    const key=document.querySelector("body > gradio-app").shadowRoot.querySelector("#ti_progress > p").innerHTML.split("Last saved image")[1].split("prompt:")[0].match(/\-[0-9]+/)[0];
    const val=document.querySelector("body > gradio-app").shadowRoot.querySelector("#ti_progress > p").innerHTML.split("Last saved image")[1].split("prompt:")[1];
    localStorage.setItem(key,val);
},10000)
```
stop
```
clearInterval(saveInterval)
```
exportAll
```
link = document.createElement( 'a' );
link.style.display = 'none';
//document.body.appendChild( link );

contents=""
for(const i in localStorage){
  contents=contents.concat(i).concat(" ").concat(localStorage[i])
}

//key code
blob = new Blob([contents], {type: 'text/txt'});  


objectURL = URL.createObjectURL(blob); 
link.href = objectURL;

link.download =  "Last.txt";
link.click();
```
you can clear All in browser history
