兼容oe7、8
`if(!Object.create){
	Object.create = function(o){
		function F(){};
		F.prototype = o;
		return new F();
	};
}
`

外部属性
`function fly(){
	alert("我飞起来了！");
}`


一只猪
`var Pig = {
		initialize:function(name){
			this.name = name;
		},
		talk:function(){
			alert("我是" + this.name);
		}
	};
`


一只红色的猪
`var	RedPig = Object.create(Pig);
	RedPig.color = '红色';
`


一只会飞的红色的猪
`var FlyableRedPig = Object.create(RedPig);
	FlyableRedPig.fly = fly;
	FlyableRedPig.swim = function(){
		alert("我还会游泳！");
	};
`


创建实例

`var pig = Object.create(FlyableRedPig);
	pig.initialize("飞天红猪侠");

pig.talk();
pig.fly();
pig.swim();
`

