# Stamped Assets
assets stamped onto bitcoin intended for use in recursive projects

| Asset Name | Stamp CPID | Description |
| -------- | ------- | ------- |
| MIT License | A4154839259198649000 | The MIT License |
| append.js | A6677669155563188000| A tiny helper library to easily load gzipped libraries into the DOM |
| [w.full.js.gz](https://github.com/xem/W ) | A10207619717431880000 | A micro WebGL2 framework with a ton of features |
| [tinyMusic.js.gz](https://github.com/kevincennis/TinyMusic/) | A10744398257522688000 | A simple, lightweight music synth/sequencer in JavaScript |
| [q5.js.gz](https://github.com/LingDong-/q5xjs) | A5297629053831280000 | q5.js is a small and fast alternative (experimental) implementation of p5.js, |
| [bonsai.min.css.gz](https://github.com/bonsaicss/bonsai.css) | A14391816994242124000 | Bonsai CSS is a super lightweight, fully responsive, utility first css framework |
| unpruneableCardsV0.js | A8302042006154452000 | A template for making recursive cards |


# Recursive Examples
### Note: The following section contains standalone HTML for example purposes.  If you do not have a stamps indexer running, you can use the web based code editor at [StampVerse.io](https://www.stampverse.io/mint/recursive-template) to make your recusive stamps.


---
---

# w.full.js.gz
This example shows a red rotating cube using the w.js library
```
<canvas id="canvas" width="800" height="800" style="aspect-ratio:${data.ratio};padding:0;margin:auto;display:block;max-width:100%;max-height:100%;position:absolute;top:0;bottom:0;left:0;right:0"></canvas>
<script>
let rotation= { x: 0, y: 0};
let speed = 0.5;

setup = () => {
	W.reset(canvas);
	W.clearColor("#ccc");
	W.camera({z:3});
	W.light({x:2,y:2,z:-2});
	W.ambient(0.1);
	W.cube({n:"cube", b:"522", rx: 45});
	draw();
}

draw = () => {
	requestAnimationFrame(draw);
	rotation.x+=speed;
	rotation.y+=speed;
	W.move({n:"cube", rx:rotation.x, ry:rotation.y});
}

window.onload = () => {
    window.appendCB = async () => {
        let add = new Append();
        try{
            await add.js(["A10207619717431880000"]);
			setup();
        }
        catch(e){
            await add.error(e,e);
        }
    }

    var s = document.createElement('script');
    s.setAttribute( 'src','/s/A6677669155563188000');
    document.body.appendChild(s);
}
</script>
```


https://github.com/user-attachments/assets/b0e9d1fe-3bf0-4526-a5c2-bb96ae6b7254




---
---
# q5.js.gz
This example shows a snowflake affect over a previously stamped image
```
<script>

// css to format the canvas to be in the center
document.head.insertAdjacentHTML("beforeend", `<style>html,body{width:100%;height:100%;margin:0;text-align:center;overflow:hidden}canvas{margin:0;width:100%;max-height:100%;object-fit:contain;image-rendering:pixelated}</style>`);

let flakes = [];

function preload() {
	avime = loadImage('/s/A13358114815176296000');
}

function setup() {
	createCanvas(150, 150);
	for (let i = 0; i < 100; i++) {
		flakes.push(new Flake(random(width), -200));
	}
}

function draw() {
	image(avime, 0, 0, width, height);
	stroke(255);
	fill(255);
	for (let i = 0; i < flakes.length; i++) {
		flakes[i].update();
	}
}

class Flake {
	constructor(x, y) {
		this.x = x;
		this.y = y;
		this.size = random(0.1, 1.5);
		this.speed = random(1, 2);
	}
  
	update() {
		this.y += this.speed;
		ellipse(this.x, this.y, this.size, this.size);
		if(this.y > height)
			this.y = 0;
	}
}

window.onload = () => {
    window.appendCB = async () => {
        let add = new Append();
        try{
            await add.js(["A5297629053831280000"]);
			new Q5("global");
        }
        catch(e){
            await add.error(e,e);
        }
    }

    var s = document.createElement('script');
    s.setAttribute( 'src','/s/A6677669155563188000');
    document.body.appendChild(s);
}
</script>
```


https://github.com/user-attachments/assets/563ee3c5-59a4-49a6-8a41-5c6ad8283914


---
---

# bonsai.css.gz

This example shows how to make an HTML card using the append library and bonsai.css 

```
<script>
window.onload = () => {
    window.appendCB = async () => {
        let add = new Append();
        try{
            await add.css(["A14391816994242124000"]);
        }
        catch(e){
            await add.error(e,e);
        }
    }

    var s = document.createElement('script');
    s.setAttribute( 'src','/s/A6677669155563188000');
    document.body.appendChild(s);
}
</script>
<div style="--cc:1; --cc-sm:2; --cc-xl:3; --cg:1.5rem; --bg:#eee; --p:1.5rem; --pos:relative; --maxh:100vh; --of:auto;">
    <figure class="accent" style="--mb:1.5rem;">
    <img src="/s/A13358114815176296000" alt="Avime">
    <figcaption>
        <h4>Avime Example</h4>
        <p>This example shows an figure using bonsai.css</p>
        <button id="button">Button</button>
    </figcaption>
    </figure>
</div>
```

![image](https://github.com/user-attachments/assets/f9a97007-cf71-48a0-87c8-cadc8864256e)

---
---
# unpruneableCardsV0.js
This example shows how a card template can be reused
```
<script>
//Unpruneable Cards - Template 0
window.data={
//mImg - Main card image cpid
mImg:"A5615166113676562000",
//bSvg - Card background svg, change fill to change color
bSvg:'<svg><rect fill="#eee" stroke="none" x="0" y="10" width="400" height="540" rx="15"></rect></svg>',
//mana - Mana bubble svg
mana:'<svg><circle r="14" cx="348" cy="56" fill="#BBB" /><text font-size="26"  x="342" y="64.5">2</text></svg>',
//titleBg - Title background color
titleBg:"#ddd",
//txtBg - Card text background color
txtBg:"#eee",
//top - Card Name
top:"Derp Herpenstein",
//mid - Card name, creature? Mana? 
mid:"Creature - Supreme Derp",
//botT - Card text, 4 lines, use &nbsp; for empty strings 
botT:[
    "Flip a coin when attacked. If heads, the ",
    "attacking creature dies and Derp is",
    "unharmed.",
    "&nbsp;"
],
//botQ - Card quote, use &nbsp; for empty string
botQ:[
    "Derp can't concentrate for more than 10",
    "seconds, but when he's concentrating...",
    'stuff happens"-Unknown',
    "&nbsp;"
],
//botC - Bottom copyright text
botC:"Derp Herpenstein (2023)",
//stats - card stats, leave as blank string if you dont want it 
stats:"1/3"
};
</script><script src=/s/A8302042006154452000></script>
```
![image](https://github.com/user-attachments/assets/273dcefa-01fb-4233-98d1-9298129b04da)

