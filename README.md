# youtube-cue
add "hot cue" points to the youtube player

```javascript
var cueStyle = document.createElement('style');
cueStyle.innerHTML += `
.cueInstantiater {
    position: relative;
    margin: 67px 0 0 12px;
}
.cueGeneralCont {
    position: absolute;
    z-index: 999999999999;
    left: 30px;
    top: 100px;
}
.cueCont {
    display: inline-block;
    vertical-align: top;
}
.cueCont + cueCont {
    margin-left: 10px;
}
`;
document.body.appendChild(cueStyle);

var video = document.querySelector('.html5-main-video');

var instantiater = document.createElement('button');
instantiater.setAttribute('class', 'cueInstantiater');
instantiater.innerHTML = 'New';
document.body.appendChild(instantiater);
    
instantiater.onclick = function(){
    instantiate();
}

var cueGeneralCont = document.createElement('div');
cueGeneralCont.setAttribute('class', 'cueGeneralCont');
document.body.appendChild(cueGeneralCont);

function instantiate(){
    var cont = document.createElement('div');
    cont.setAttribute('class', 'cueCont');
    cueGeneralCont.appendChild(cont);

    var trigger = document.createElement('button');
    trigger.innerHTML = video.currentTime;
    cont.appendChild(trigger);
    
    trigger.onclick = function(){
        video.currentTime = this.innerHTML;
    }
    
    var remove = document.createElement('button');
    remove.innerHTML = 'x';
    cont.appendChild(remove);
    
    remove.onclick = function(){
        cont.remove();
    }
}
```



