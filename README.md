# hydra_sketches
Various Hydra sketches I've done since 2021 - Carl Testa

```
//10.23.2021
var stuff = 
    osc(10,0.1,1.5)
	.modulateRotate(osc(10,0.5),0.9)
	.luma(0.5,0.1)
	.scrollX(0.5,0.1)
	.scrollY(0.5,0.1)
	.color(1,0,1)
	.modulate(noise(10,0.90))
	.brightness(()=>Math.sin(time*0.1));

src(o0).blend(stuff, 0.005).out(o0);
```
```
voronoi().color(1,0,1)
	.modulate(voronoi().color(1,1,0),0.7)
	.diff(osc(5,0.1,1))
	.modulate(noise(0.6),0.8)
	.modulate(osc(5,0.1),0.9)
	.out()
```
```
osc(1,0.1,1)
	.blend(noise(0.1).modulateRotate(voronoi(10),0.9),0.9)
	.modulateKaleid(osc(20),0.9)
	.color(1,0.6,1)
	.out()
```
```
osc(10,0.2,1.5)
	.modulate(voronoi(3,1),0.9)
	.modulateKaleid(noise(0.2))
	.out()
```
```
//portal
//carl testa 10/29/2021

noise(3,0.1)
.rotate(1,0.1)
.modulateKaleid(osc(10,0.1,1.5))
.add(osc(1,1,1.5))
.out()
```

```
//Space
//@carltesta

speed=1;
function pulse (begin, numitems, step) {
  //const arr = Array.from({length: numitems}, (_, index) => begin + step);
  //arr = Array.from({length: numitems}, (x, i) => start + (step * i))
  
  //create an array of specified length
  const arr1 = Array.from({length: numitems}, (x, i) => i);
  const arr2 = arr1.reverse;
  //multiply the array to scale it to the appropriate values
  //arr = arr
  const arr3 = arr1.concat(arr2); 
//  start + (step * i)
  return arr2
  console.log(arr2)
}

noise(1000)
  .luma(0.9,0.1)
//Sun
  .mask(shape(100,0.2,0.1).color(1,1,1,0).invert())
  .add(shape(100,0.2,pulse).color(1,0,0))
  .add(shape(100,0.2,0.1).color(1,0.8,0,0.2),1).scrollX(-0.3,0).scrollY(0.3,0)
//Purple Star
  .mask(shape(100,0.05,0.1).color(1,1,1,0).invert())
  .add(shape(100,0.05,0.12).color(1,0,1))
  .add(shape(100,0.05,0.1).color(0,0.9,0.5)).scrollX(0.2,0).scrollY(-0.1,0)
  .out()
```

```
var rate = 0.05;
noise(1000)
  .luma(0.9,0.1)
.out(o3)
//Sun
  shape(100,0.2,0.1).color(0,1,0,0)
  .add(shape(100,0.22,0.11).color(1,0,0))
  .add(shape(100,0.2,0.1).color(1,0.8,0,0.2),1).scrollX(-0.3,0.1*rate).scrollY(0.3,0.2*rate)
.out(o2)
//Purple Star
 shape(100,0.05,0.1).color(0,1,0,1)
  .add(shape(100,0.05,0.12).color(1,0,1))
  .add(shape(100,0.05,0.1).color(0,0.9,0.5)).scrollX(0.2,0.12*rate).scrollY(-0.1,0.13*rate)
.out(o1)
src(o3).add(src(o2),1).add(src(o1),1)
.out(o0)
```

```
//The More You Know
//@carltesta

osc(10,0.1,1.5)
  .rotate(0.01,0.01)
  .luma(0.1,0.9)
  .add(noise(100).luma(0.9,0.1))
  .add(shape(5,0.05,0.6).scrollX(0.5,0.01).scrollY(0.11,0.02))
  .out()
```

```
//More Nightscapes
//@carltesta

gradient(0.1)
	.modulate(noise(10, 0.01).thresh(0.6).scrollX(0, 0.01).scrollY(0, 0.011), 0.9)
	.modulateScale(osc(1), 0.9)
	.rotate(1, 0.1)
	.add(noise(100).luma(0.9, 0.1))
	.blend(osc(10).color(1, 0, 1).modulateRotate(noise(), 0.2), 0.25)
	.out()
```
```
//12/3/2021
speed=4;
osc(1, 0.1, 1.5)
	.modulateRotate(osc(50, 0.1, 1.5), 0.9)
	.modulateKaleid(osc(0.1, 0.1, 1.5), 0.9)
	.rotate(1, 0.1)
	.modulate(o0, 0.9)
	.out()
```
```
//neat
noise(1).add(voronoi(10).modulateScale(osc(10,0.1,1.5),0.9),0.5).add(osc(1,1,1.5),0.5).rotate(1,1).modulateScale(gradient(), 0.9).add(shape().modulate(noise(3),0.1),0.5).scale(0.003).blend(solid(),0).out() 
```
```
//Wild

shape([3].fast(20)).color(1,1,0).modulateScale(noise(5),0.5)
.blend(shape([1,2,3,4,5,6,7,8,9,10,11,12].fast(10)).color(1,0,1).repeat([1,2,3,4,5,6],[1,2,3,4,5]),0.5)
.colorama(()=>Math.sin(time/16))
     .out()
```

```
//12/22/2021

osc()
  .layer(noise(10).mask(shape([3].smooth()).rotate(1,1)).scrollX(0.9,0.2).scrollY(0.1,0.4).scale(1))
.blend(o0,0.9)
  .out()
```

```
12/31/2021

p = new P5({mode: 'WEBGL'})
p.draw=()=>{
p.background(0,0,0,0);  
//p.orbitControl(10,10,10);

p.rotateX(time * 0.5);
  p.rotateY(time *0.5);
  p.fill(255,255,255);  
p.torus(700,300,5);

}
p.hide();

s0.init({src:p.canvas})

osc(20,0.1,1.5).mult(src(s0).modulateRotate(o0,0.9)).out()
```
```
4/25/2022
voronoi(1).modulate(osc(1.5,0.1,1.5),0.9).mult(noise(0.9).mult(osc(0.01,7000,0))).rotate(1,0.1).out()
```
```
4/16/2022
osc(10,0.1,1.5).mult(shape(3,0.25,0.5).rotate(1,0.1)).modulate(src(o0),0.9).out(o0)
```
```
4/11/2022
noise(1.5).mult(osc(2,0.1,1.5).modulateRotate(osc(10,0.1,1.5),0.9)).mult(osc(0.5,0.1,1.5)).out()
```
```
3/2/2022
voronoi(()=>cc[20]*50).rotate(()=>cc[16]).scroll(0.1,0.1,()=>cc[18],()=>cc[19])
  .modulate(osc(5,0.1,1.5).mult(noise(()=>cc[21]*25).rotate(()=>cc[17]*5)),()=>cc[23])
.blend(solid(1,0,0),()=>cc[32]/2)
.blend(solid(0,1,0),()=>cc[33]/2)
.blend(solid(0,0,1),()=>cc[34]/2)
  .out()
```
```
2/3/2022
osc(5,0.1,1.5).rotate(1,0.1).modulate(noise(0.5),0.8).mult(voronoi()).posterize().out()
```
```
osc(5,0.1,1.5).rotate(1,0.1).modulate(noise(0.5),0.9).mult(voronoi(1)).posterize(10).contrast(0.9).out()
```
```
osc(5,0.1,1.5).rotate(1,0.1).modulate(noise(0.5),0.9).mult(voronoi(1)).posterize().saturate(50).out()
```
