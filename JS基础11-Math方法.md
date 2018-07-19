## Mtah中常用的方法

> 数学函数，但是它是对象数据类型`typeof Math -> 'object'`
> 
> Math对象中给我们提供了很多常用操作数字的方法
> 
> `console.dir(Math)`查看所有方法

> 常用方法：

`abs`

```javascript	
Math.abs('-1');     // 1
Math.abs(-2);       // 2
Math.abs(null);     // 0
Math.abs('');       // 0
Math.abs([]);       // 0
Math.abs([2]);      // 2
Math.abs([1,2]);    // NaN
Math.abs({});       // NaN
Math.abs('string'); // NaN
Math.abs();         // NaN
```

`ceil` && `floor`

```javascript
Math.ceil(.95);    // 1
Math.ceil(4);      // 4
Math.ceil(7.004);  // 8
Math.ceil(-0.95);  // -0
Math.ceil(-4);     // -4
Math.ceil(-7.004); // -7

Math.floor( 45.95); //  45
Math.floor( 45.05); //  45
Math.floor(  4   ); //   4
Math.floor(-45.05); // -46 
Math.floor(-45.95); // -46
```

`round`

```javascript
Math.round( 20.49); //  20
Math.round( 20.5 ); //  21
Math.round( 42   ); //  42
Math.round(-20.5 ); // -20
Math.round(-20.51); // -21
```

`random` ： 生成随机数

```javascript
Math.random(); 生成0-1之间的随机数
```

`max` && `min`

```javascript
Math.max(10, 20);   //  20
Math.max(-10, -20); // -10
Math.max(-10, 20);  //  20

Math.min(10, 20);   //  10
Math.min(-10, -20); // -20
Math.min(-10, 20);  //  -10
```

`PI` 圆周率

`pow` && `sqrt` 

Math.sqrt(number) :如果number为负值，则返回NaN

```javascript
Math.pow(7, 2);    // 49
Math.pow(7, 3);    // 343
Math.pow(2, 10);   // 1024
// fractional exponents
Math.pow(4, 0.5);  // 2 (square root of 4)
Math.pow(8, 1/3);  // 2 (cube root of 8)
Math.pow(2, 0.5);  // 1.4142135623730951 (square root of 2)
Math.pow(2, 1/3);  // 1.2599210498948732 (cube root of 2)
// signed exponents
Math.pow(7, -2);   // 0.02040816326530612 (1/49)
Math.pow(8, -1/3); // 0.5
// signed bases
Math.pow(-7, 2);   // 49 (squares are positive)
Math.pow(-7, 3);   // -343 (cubes can be negative)
Math.pow(-7, 0.5); // NaN (negative numbers don't have a real square root)
// due to "even" and "odd" roots laying close to each other, 
// and limits in the floating number precision, 
// negative bases with fractional exponents always return NaN
Math.pow(-7, 1/3); // NaN

Math.sqrt(9); // 3
Math.sqrt(2); // 1.414213562373095
Math.sqrt(1);  // 1
Math.sqrt(0);  // 0
Math.sqrt(-1); // NaN
```