<template>
  <div id="souvenir">
      <a style="font-size:30px; padding-left:30px;" href="/">Back to main</a>
      <div v-if="main_enable == false"><h1>CPE SOUVENIR SHOP</h1></div>
      <div v-if="main_enable == true" class="row" style="padding-top:40px; padding-left:200px; padding-right:200px; display: grid; grid-template-columns: 50% 50%">
        <img style="padding-top:20px; padding-left:400px; width:150px;" v-for="item in reun" :key="item.img" :src="items[item_selected.display_order[0]].img" />
        <div style="text-align:left;">
          <h1>{{items[item_selected.display_order[0]].name}}</h1>
          <p>฿{{items[item_selected.display_order[0]].price}}</p>
          <p>{{items[item_selected.display_order[0]].description}}</p>
          <div style="margin-left:20px; display: inline-block;" v-if="items[item_selected.display_order[0]].colors != null">
            <label for="myCheck">Color:</label>
            <div style="display: inline-block;" v-for="(color, index) in items[item_selected.display_order[0]].colors" :key="index">
              <input type="radio" name="color" :id="color" v-model="item_selected.color" :value="color">{{color}}
            </div>
          </div>
          <div>
            <!-- <button disabled >ADD TO CART</button> -->
            <br>
            <div style="padding:5px; width:140px; background-color:#FFFFFF; border-radius: 15px; border:2px; border-style: solid; border-color:#000000;">
              <a style="margin-left:10px; color:#000000; letter-spacing: 1.6px; font-size:18px; font-family: 'CloudBold';" target="_blank" v-bind:href="items[item_selected.display_order[0]].link">GO TO SHOP</a>
            </div>
          </div>
        </div>
      </div>
      <div class="row" style="padding-top:40px; padding-left:200px; padding-right:200px;">
          <h1 style="margin-bottom:40px; text-align:center;" v-if="main_enable == false">OUR PRODUCTS</h1>
          <h1 style="margin-bottom:40px; text-align:center;" v-if="main_enable == true">OTHER PRODUCTS</h1>
          <div style="display: flex; justify-content: center; align-items: center;}">
              <div style="margin-left:20px; display: inline-block;" v-if="main_enable == false" @click="sortItemOrder(item_selected.display_order[0]);main_enable=true">
                <img style="width:120px;" v-for="item in reun" :key="item.img" :src="items[item_selected.display_order[0]].img" />
                <p>{{items[item_selected.display_order[0]].name}}</p>
                <p>฿{{items[item_selected.display_order[0]].price}}</p>
              </div>
              <div style="margin-left:20px; display: inline-block;" @click="sortItemOrder(item_selected.display_order[1]);main_enable=true">
                <img style="width:120px;" v-for="item in reun" :key="item.img" :src="items[item_selected.display_order[1]].img" />
                <p>{{items[item_selected.display_order[1]].name}}</p>
                <p>฿{{items[item_selected.display_order[1]].price}}</p>
              </div>
              <div style="margin-left:100px; display: inline-block;" @click="sortItemOrder(item_selected.display_order[2]);main_enable=true">
                <img style="width:120px;" v-for="item in reun" :key="item.img" :src="items[item_selected.display_order[2]].img" />
                <p>{{items[item_selected.display_order[2]].name}}</p>
                <p>฿{{items[item_selected.display_order[2]].price}}</p>
              </div>
              <div style="margin-left:100px; display: inline-block;" @click="sortItemOrder(item_selected.display_order[3]);main_enable=true">
                <img style="width:120px;" v-for="item in reun" :key="item.img" :src="items[item_selected.display_order[3]].img" />
                <p>{{items[item_selected.display_order[3]].name}}</p>
                <p>฿{{items[item_selected.display_order[3]].price}}</p>
              </div>
              <div style="margin-left:100px; display: inline-block;" @click="sortItemOrder(item_selected.display_order[4]);main_enable=true">
                <img style="width:120px;" v-for="item in reun" :key="item.img" :src="items[item_selected.display_order[4]].img" />
                <p>{{items[item_selected.display_order[4]].name}}</p>
                <p>฿{{items[item_selected.display_order[4]].price}}</p>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'souvenir',
  data() {
    return {
      main_enable:false,
      item_selected:{
        display_order: [0,1,2,3,4],
        color:"",
      },
      items:[
        {
        id:1,
        name:"Screen Shirt",
        price:100,
        colors:['Red','Blue'],
        description:"Lorem ipsum dolor sit amet, consectetur adipiscing elit",
        link:"https://shopee.co.th/%E0%B9%80%E0%B8%AA%E0%B8%B7%E0%B9%89%E0%B8%AD%E0%B9%82%E0%B8%9B%E0%B9%82%E0%B8%A5%E0%B8%AA%E0%B8%B5%E0%B9%80%E0%B8%AB%E0%B8%A5%E0%B8%B7%E0%B8%AD%E0%B8%87%E0%B8%9B%E0%B8%B1%E0%B9%88%E0%B8%99%E0%B9%80%E0%B8%9E%E0%B8%B7%E0%B9%88%E0%B8%AD%E0%B8%9E%E0%B9%88%E0%B8%AD-%E0%B8%81%E0%B8%A5%E0%B8%B1%E0%B8%9A%E0%B8%A1%E0%B8%B2%E0%B8%AD%E0%B8%B5%E0%B8%81%E0%B8%84%E0%B8%A3%E0%B8%B1%E0%B9%89%E0%B8%87-%E0%B9%80%E0%B8%AA%E0%B8%B7%E0%B9%89%E0%B8%AD%E0%B9%80%E0%B8%AB%E0%B8%A5%E0%B8%B7%E0%B8%AD%E0%B8%87-%E0%B9%81%E0%B8%82%E0%B8%99%E0%B8%9F%E0%B9%89%E0%B8%B2-i.214880.714086943",
        img:require("@/assets/TestCatalog/screenshirt.jpg")

        },
        {
        id:2,
        name:"Shirt",
        price:200,
        colors:['Pink','White'],
        description:"Lorem ipsum dolor sit amet, consectetur adipiscing elit",
        link:"https://shopee.co.th/%E0%B9%80%E0%B8%AA%E0%B8%B7%E0%B9%89%E0%B8%AD%F0%9F%92%A5%E0%B9%82%E0%B8%9B%E0%B9%82%E0%B8%A5-bike-for-Mom-%F0%9F%92%A5%E0%B8%82%E0%B8%AD%E0%B8%87%E0%B8%A3%E0%B9%89%E0%B8%B2%E0%B8%99%E0%B8%A1%E0%B8%B5%E0%B8%9F%E0%B9%89%E0%B8%B2-%E0%B8%A3%E0%B8%B2%E0%B8%84%E0%B8%B2%E0%B8%9E%E0%B8%B4%E0%B9%80%E0%B8%A8%E0%B8%A9%E2%9D%A4%EF%B8%8F-i.117400.617813",
        img:require("@/assets/TestCatalog/shirt.jpg")
        },
        {
        id:3,
        name:"Polo Shirt",
        price:300,
        colors:['Red','Blue'],
        description:"Lorem ipsum dolor sit amet, consectetur adipiscing elit",
        link:"https://shopee.co.th/%E0%B9%80%E0%B8%AA%E0%B8%B7%E0%B9%89%E0%B8%AD%E0%B9%82%E0%B8%9B%E0%B9%82%E0%B8%A5%E0%B8%94%E0%B8%B3-%E0%B9%80%E0%B8%AA%E0%B8%B7%E0%B9%89%E0%B8%AD%E0%B8%94%E0%B8%B3-%E0%B9%82%E0%B8%9B%E0%B9%82%E0%B8%A5%E0%B8%94%E0%B8%B3-%E0%B9%80%E0%B8%AA%E0%B8%B7%E0%B9%89%E0%B8%AD%E0%B9%82%E0%B8%9B%E0%B9%82%E0%B8%A5-%E0%B8%A3%E0%B8%B2%E0%B8%84%E0%B8%B2%E0%B9%80%E0%B8%A3%E0%B8%B4%E0%B9%88%E0%B8%A1%E0%B8%95%E0%B9%89%E0%B8%99100%E0%B8%BF-i.10421295.547247038",
        img:require("@/assets/TestCatalog/polo.png")
        },
        {
        id:4,
        name:"Cloth Bag",
        price:400,
        colors:null,
        description:"Lorem ipsum dolor sit amet, consectetur adipiscing elit",
        link:"https://shopee.co.th/%F0%9F%92%A5%E0%B8%81%E0%B8%A3%E0%B8%B0%E0%B9%80%E0%B8%9B%E0%B9%8B%E0%B8%B2%E2%80%8B%E0%B8%9C%E0%B9%89%E0%B8%B2-%E0%B8%A5%E0%B8%94%E0%B9%82%E0%B8%A5%E0%B8%81%E0%B8%A3%E0%B9%89%E0%B8%AD%E0%B8%99-%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99-%E0%B8%A5%E0%B8%B2%E0%B8%A2%E0%B8%98%E0%B8%87%E0%B8%8A%E0%B8%B2%E0%B8%95%E0%B8%B4%E2%80%8B%E0%B9%84%E0%B8%97%E0%B8%A2-%E0%B8%9E%E0%B8%B4%E0%B8%A1%E0%B8%9E%E0%B9%8C%E2%80%8B%E0%B8%84%E0%B8%B3%E0%B8%A7%E0%B9%88%E0%B8%B2%E2%80%8B-%E0%B8%AB%E0%B8%A2%E0%B8%B8%E0%B8%94%E2%80%8B%E0%B9%80%E0%B8%8A%E0%B8%B7%E0%B9%89%E0%B8%AD%E2%80%8B%E0%B9%80%E0%B8%9E%E0%B8%B7%E0%B9%88%E0%B8%AD%E2%80%8B%E0%B8%8A%E0%B8%B2%E0%B8%95%E0%B8%B4%E2%80%8B-i.93094179.6041700644",
        img:require("@/assets/TestCatalog/clothbag.png")
        },
        {
        id:5,
        name:"Sticker",
        price:500,
        colors:null,
        description:"Lorem ipsum dolor sit amet, consectetur adipiscing elit",
        link:"https://shopee.co.th/%E0%B8%AA%E0%B8%95%E0%B8%B4%E0%B8%81%E0%B9%80%E0%B8%81%E0%B8%AD%E0%B8%A3%E0%B9%8C%E0%B8%95%E0%B8%B4%E0%B8%94%E0%B8%A3%E0%B8%96-%E0%B8%A7%E0%B8%B1%E0%B8%A2%E0%B8%A3%E0%B8%B8%E0%B9%88%E0%B8%99%E0%B8%AA%E0%B8%A3%E0%B9%89%E0%B8%B2%E0%B8%87%E0%B8%95%E0%B8%B1%E0%B8%A7-1-%E0%B9%81%E0%B8%9C%E0%B9%88%E0%B8%99-%E0%B8%AA%E0%B8%95%E0%B8%B4%E0%B8%81%E0%B9%80%E0%B8%81%E0%B8%AD%E0%B8%A3%E0%B9%8C%E0%B8%84%E0%B8%B3%E0%B8%84%E0%B8%A1-%E0%B8%AA%E0%B8%95%E0%B8%B4%E0%B8%81%E0%B9%80%E0%B8%81%E0%B8%AD%E0%B8%A3%E0%B9%8C%E0%B8%84%E0%B8%B3%E0%B8%81%E0%B8%A7%E0%B8%99-Teen004-%E0%B8%AA%E0%B8%95%E0%B8%B4%E0%B9%8A%E0%B8%81%E0%B9%80%E0%B8%81%E0%B8%AD%E0%B8%A3%E0%B9%8C%E0%B8%95%E0%B8%B4%E0%B8%94%E0%B8%A3%E0%B8%96-%E0%B8%AA%E0%B8%95%E0%B8%B4%E0%B8%81%E0%B9%80%E0%B8%81%E0%B8%AD%E0%B8%A3%E0%B9%8C%E0%B9%80%E0%B8%97%E0%B9%88%E0%B9%86-%E0%B8%AA%E0%B8%95%E0%B8%B4%E0%B8%81%E0%B9%80%E0%B8%81%E0%B8%AD%E0%B8%A3%E0%B9%8C%E0%B9%81%E0%B8%95%E0%B9%88%E0%B8%87-i.323486427.5058608339",
        img:require("@/assets/TestCatalog/sticker.jpg")
        }
      ],
    reun:[0]
    }
  },
  methods: {
  sortItemOrder(clickIndex) {
      if(clickIndex == 0) {
        this.item_selected.display_order = [0,1,2,3,4];
      }
      else if(clickIndex == 1) {
        this.item_selected.display_order = [1,0,2,3,4];
      }
      else if(clickIndex == 2) {
        this.item_selected.display_order = [2,0,1,3,4];
      }
      else if(clickIndex == 3) {
        this.item_selected.display_order = [3,0,1,2,4];
      }
      else if(clickIndex == 4) {
        this.item_selected.display_order = [4,0,1,2,3];
      }
      this.item_selected.color = "";
     }
  }
}
</script>

<style scoped>
  a {
      text-decoration: none;
  }

  .button{
    padding: 10px;
    font-size: 30px;
  }
</style>