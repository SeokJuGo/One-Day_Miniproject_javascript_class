# ๐ Java Script One-Day Mini Project ๐
### ๐๏ธ 2023๋ 2์ 6์ผ ~ 2023๋ 2์ 6์ผ


<div align='center'>
</div>
<br/>

## ํ์ ๐
- ๊ณ ์์ฃผ
- ์ฃผํ์
- ์ ํ์ค



## ๋ชฉ์ฐจ :bookmark_tabs:
- [๊ฐ๋ฐ์ธ์ด](#๊ฐ๋ฐ์ธ์ด)


- [๊ฐ์](#๊ฐ์)


- [์์ฐ์์](#์์ฐ์์)


- [ERD](#ERD)


- [์ฝ๋](#์ฝ๋)


- [์ถ๊ฐ๊ธฐ๋ฅ](#์ถ๊ฐํ๊ณ ์ถ์๊ธฐ๋ฅ)

## ๊ฐ๋ฐ์ธ์ด
- JavaScript
- HTML
- CSS

## ๊ฐ์

#### ๋ง์ผ ์ปฌ๋ฆฌ ์ฌ์ดํธ์ ๊ณ ๊ฐ ์ ๋ณด๋ฅผ ํ์ธ ํ ๋ฑ๊ธ์ ๋ง๋ ์๋น์ค ๊ฐ์ฒดํํด์ ๋ง๋ค๊ธฐ 

## ์์ฐ์์
![market](https://user-images.githubusercontent.com/116260619/217056358-a6dea18c-0c63-43d9-9c6e-64380146e47a.gif)
### ์ค๋ฅธ์ชฝ ํ๋จ์ total์ด ๋์ ๋๋ค.(Cart UI๋ ๋ฏธ์์ฑ)


### ๋งํฌ https://seokjugo.github.io/One-Day_Miniproject_javascript_class/


![market2](https://user-images.githubusercontent.com/116260619/217057905-d0f9e113-9339-4c63-bbb9-a143e51eba1b.gif)

## ERD
![image](https://user-images.githubusercontent.com/116260619/217052540-06b293d9-350d-411d-809f-a7aeb76c27c5.png)

#### ์ธ ๊ฐ์ ํด๋์ค๋ก ๊ตฌ์ฑ

> Member Class

- name ๊ณ ๊ฐ์ด๋ฆ 
- total ์ด ๊ฒฐ์  ๊ธ์ก
- reward ์ ๋ฆฝ๊ธ
- delivery fee ๋ฐฐ๋ฌ๋ฃ



> Product
- p_num ์ ํ๋ฒํธ
- p_name ์ ํ์ด๋ฆ
- p_quantity ์๋
- jjim ์ฐ


> Cart
- p_num ์ ํ๋ฒํธ
- c_num ์นดํธ๋ฒํธ
- quantity ์นดํธ์ ๋ค์ด๊ฐ ์๋ ์๋






## Trouble Shooting
- 





## ์ฝ๋
```
class Member {
    constructor(name) {
      this.name = name;
      this.total = 0;
      this.reward = 0;
      this.delivery_fee = 3000;
      this.cart = new Cart();
    }
      info() {
      console.log(`์ด๋ฆ: ${this.name}`);
    }
      buy(product,value=1) {
        this.total += product.p_price*value;
        product.quantity-=value
        console.log(`${this.name}๋์ด ${product.p_name}(โฉ${product.p_price*value})๋ฅผ ${value}๊ฐ ์์ต๋๋ค!`);
    }
      add_cart(product, quantity) {
        this.cart.add_item(product, quantity);
      }
       delete_cart(product) {
         this.cart.delete_item(product);
    }
      get_cart() {
        return this.cart;
      }
   }
  // 0. ์กฐ๊ฑด: ๋ฑ๊ธ์ ์ผ๋ฐํ์, ํ๋ ์ฆ, ํผํ(Plain, Friends, Purple) + ๊ฐ์ธ์ ๋ณด๋ ์ด๋ฆ๋ง ๋ฐ์ต๋๋ค. ์ด์ธ 3๊ฐ ํด๋์ค๋ฅผ ๊ตฌํํ๋๋ฐ ํ์ํ ์์ฑ, ํจ์๋ฅผ ์ง์  ๋ผ์ํ๊ณ  ๊ตฌํํด๋ณด์ธ์
  class PlainMember extends Member {
    constructor(name,total,reward,delivery_fee) {
      super(name,total,reward,delivery_fee);
      reward=this.total*0.005;
    }
    info_check(){
      super.info();
      this.reward=Math.floor(this.total*0.005);
      console.log(`์ด ๊ตฌ๋งค๊ธ์ก : โฉ${this.total} , ์ ๋ฆฝ๊ธ : โฉ${this.reward}, ํ์๋ฑ๊ธ๋ฒํธ: ์ผ๋ฐ, ๋ฐฐ์ก๋น :${this.delivery_fee}์`);
    }
  }
  class FriendsMember extends Member {
    constructor(name,total,reward,delivery_fee) {
      super(name,total,reward);
      reward=this.total*0.01;
      this.delivery_fee=2000;
    }
    info_check(){
      super.info();
      this.reward=Math.floor(this.total*0.01);
      console.log(`์ด ๊ตฌ๋งค๊ธ์ก : โฉ${this.total} , ์ ๋ฆฝ๊ธ : โฉ${this.reward}, ํ์๋ฑ๊ธ๋ฒํธ: ํ๋ ์ฆ , ๋ฐฐ์ก๋น :${this.delivery_fee}์`);
    }
  }
  class PurpleMember extends Member {
    constructor(name,total,reward,delivery_fee) {
      super(name,total,reward);
      this.delivery_fee=0;
      reward=this.total*0.07;
    }
     info_check(){
      super.info();
      this.reward=Math.floor(this.total*0.07);
      console.log(`์ด ๊ตฌ๋งค๊ธ์ก : โฉ${this.total} , ์ ๋ฆฝ๊ธ : โฉ${this.reward}, ํ์๋ฑ๊ธ๋ฒํธ: ํผํ , ๋ฐฐ์ก๋น :${this.delivery_fee}์`);
    }
  }
  // 1. ์ผ๋ จ๋ฒํธ, ์ํ๋ช, ์๋, ๊ฐ๊ฒฉ์ ์์ฑ์ผ๋ก ๊ฐ์ง๋ Product ํด๋์ค๋ฅผ ๊ตฌํํด๋ณด์ธ์. (์ผ๋ จ๋ฒํธ๋ ์๋ ์๋ ฅ๋จ)
  class Product {
    static product_num = 0;
    constructor(p_name, p_quantity, p_price,jjim=0) {
      this.p_num = ++Product.product_num;
      this.p_name = p_name;
      this.p_quantity = p_quantity;
      this.p_price = p_price;
      this.jjim = jjim;
    }
    get num() {
      return this.p_num;
    }
    get name() {
      return this.p_name;
    }
    set name(value) {
      this.p_name = value;
    }
    get quantity() {
      return this.p_quantity;
    }
    set quantity(value) {
      this.p_quantity = value;
    }
    get price() {
      return this.p_price;
    }
    set price(value) {
      this.p_price = value;
    }
  }
  class Cart {
    constructor() {
      this.items = [];
    }
    add_item(product, quantity) {
      let exist = this.items.find(i => i.product.name === product.name);
      if (exist) {
        exist.quantity += quantity;
      } else {
        this.items.push({ product, quantity });
      }
    }
    delete_item(product) {
      this.items.pop({product});
    }
    get_items() {
      return this.items;
    }
  }
  // Go๋ ์ผ๋ฐํ์
  const Go = new PlainMember("SeokJu");
  // Joo๋ ํ๋ ์ฆํ์
  const Joo = new FriendsMember("Hansol");
  // Jeon์ ํผํํ์
  const Jeon = new PurpleMember("hyunjun");
  const apple = new Product("์ฌ๊ณผ", 10, 1500);
  const mouse= new Product("๋ง์ฐ์ค", 20, 20000);
  const notebook = new Product("๋ธํธ๋ถ", 10, 300000);
```

![image](https://user-images.githubusercontent.com/116260619/217062224-8cb6232f-8360-4380-9cfa-1e4606bbd52f.png)
### 1. Cart ํด๋์ค ์ถ๊ฐ, ์ ํ, ์ด๋ฆ์ ๋ด์ ๊ฐ์ฒด๋ค์ ์ฌ๋ฌ ๊ฐ ๋ถ๋ฌ์ค๊ณ  ์ง์



![image](https://user-images.githubusercontent.com/116260619/217061515-c99fec8a-5097-477d-b2a6-4ddff69bce90.png)
### 2. reward, delivery fee ๋ณ์๋ก ์์๋ฐ์ Memeber ๋ฑ๊ธ๋ณ ์ฐจ๋ฑ ๋ถ์ฌ



![image](https://user-images.githubusercontent.com/116260619/217061930-808ac2f5-1c48-4c96-9e8c-e47854aeb2e1.png)
### 3. buy ๋งค๊ฐ๋ณ์ value=1 ๊ธฐ๋ณธ๊ฐ์ผ๋ก ํจ์ผ๋ก์จ ์๋์ ์๋ ฅ ์ ํ๋ง ์๋ ฅ ์์๋ ํ๋ ์ฉ ๊ตฌ๋งค



## ์ถ๊ฐํ๊ณ ์ถ์๊ธฐ๋ฅ
- ๋ฐ์ดํฐ๋ฒ ์ด์ค ์ถ๊ฐ (fireabase or mysql)
- ๋ฐ์ํ์ผ๋ก ์ ํ๋ณ ์ฐ ์ถ๊ฐ ํ ์ฌ์ฉ์๊ฐ ์ํ  ์ ๋ฆฌ๋ค์ด๋ ์ ๋ฆฌ์คํธ ๋์ดํ๊ธฐ
- Cart ๋ชฉ๋ก ์ ์ฒด ๊ตฌ๋งคํ๊ธฐ
- UI๋ก Cart ๋ชฉ๋ก(์ด๋ฆ, ๊ฐ์) ๋์ดํ๊ธฐ
- Member_detail ํด๋์ค ์์ฑํ๊ธฐ
