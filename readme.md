对比一下老龙的简易的JS OOP 类和继承 [https://github.com/huya-fed/class/blob/master/README.md](https://github.com/huya-fed/class/blob/master/README.md "老龙的简易的JS OOP 类和继承")

## 对象行为委托或许更简单些，不用加载外部库，思路也更简单些。 ##
## 虽然它看似只是一个 Object.create，但可以实现同样功能且通俗易懂，何乐而不为。 ##


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

