<template>
  <div class="container">
    <header>How Maney?</header>

    <h3>
      [How Maney?]をお使いいただき<br>
      誠にありがとうございます。<br>
      このアプリでは金銭を計算できます。
    </h3>

    <p>合計金額：{{ sum }}円</p>
    <table class="main">
      <tr v-for="item in items" :key="item.value">
        <td>{{ item.value }}円</td>
        <td>
          <input type="number" v-model="item.num">
        </td>
      </tr>
    </table>
    <footer></footer>
  </div>
</template>


<script>
export default {
  data() {
    return {
      items: [1, 5, 10, 50, 100, 500, 1000 ,2000, 5000, 10000].map(value => ({ num: 0, value }))
    };
  },
  computed: {
    sum() {
      return this.items
      .map(item => item.num * item.value)
      .reduce((result, price) => result + price, 0 )
    }
  }
};
</script>
<style lang="scss">
  header {
    background-color:cadetblue;
    color: aliceblue;
    padding: 20px;
    font-size: 30px;
  }

  h3{
    text-align: center;
    color: navy;
    margin-top: 5px;
  }

  p {
    margin: 0 auto;
    padding: 20px 0 20px 0;
    background-color: plum;
    width: 40%;
    text-align: center;
  }

  table {
    font-size: 30px;
    border: 1px black solid;
    background-color:dimgray;

    td{
      text-align: center;
      border: 1px black solid;
      background-color: darkblue;
      color: white;
    }
  }
  
  .main {
    width: 70%;
    margin: 15px auto 15px auto;
  }
  footer {
    background-color:cadetblue;
    color: aliceblue;
    padding: 25px;
  }

  @media screen and (max-width: 900px) {
    .main {
      width: 100%;
      margin: 15px auto 0px auto;
    }
  }
</style>
