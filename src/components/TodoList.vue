<template>
  <main>
    <section class="to-do">
      <div class="input">
        <input class="text" name="text" type="text" placeholder="Digite" value="item" v-model="item" ref="input" @keyup.enter="addItem"> 
        <button class="add" @click.prevent="addItem">
          <img src="../assets/ic-add.png" alt="Ilustração Adicionar">
        </button>
      </div>

      <div class="items-vazio" v-if="!arrayItems.length">
        <p>Nenhum item cadastrado</p>
      </div>

      <div class="items" v-else>
        <ul>
          <li v-for="(item, index) in arrayItems" :key="index" ref="teste">
            <p>{{item}}</p>
            <button @click.prevent="removeItem(index)">
              <img src="../assets/ic-delete.png" alt="Ilustração Remover">
            </button>
          </li>
        </ul>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: 'TodoList',
  data() {
    return {
      item: '',
      arrayItems: []
    };
  },
   methods: {
    addItem() {
      if(!this.item) return;

      this.arrayItems.push(this.item);
      this.item = "";
    },
    removeItem(index) {
      this.arrayItems.splice(index, 1);
      
      console.log(index)

      console.log(this.$refs.teste)
		}
  },
}
</script>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

main {
  display: flex;
  width: 100%;
  height: 100vh;
  justify-content: center;
  align-items: center;
  font-family: 'Roboto', sans-serif;
}

.to-do {
  width: 400px;
  height: 400px;
  background: #FFFFFF;
  box-shadow: 0px 1px 4px rgba(0, 0, 0, 0.25);
  border-radius: 4px;
  padding: 24px;
  box-sizing: border-box;
}

.input {
  display: flex;
  width: 100%;
  position: relative;
}

.input .text {
  background: #FFFFFF;
  box-shadow: 0px 1px 4px rgba(0, 0, 0, 0.25);
  border-radius: 2px;
  width: 288px;
  height: 48px;
  padding-left: 16px;
  font-family: 'Roboto', sans-serif;
  color: #303030;
  font-size: 16px;
  line-height: 19px;
  box-sizing: border-box;
}

::-webkit-input-placeholder {color: #909090;}

:-ms-input-placeholder {color: #909090;}

::placeholder {color: #909090;}

.input .add {
  display: flex;
  justify-content: center;
  align-items: center;
  background: #40D9B8;
  border-radius: 100px;
  width: 48px;
  height: 48px;
  position: absolute;
  right: 0;
}

.input .add img {
  width: 24px;
  height: 24px;
}

.items-vazio {
  width: 352px;
  height: 280px;
  margin-top: 24px;
  background: #F2F2F2;
  border: 1px dashed #CCCCCC;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
}

.items-vazio p {
  font-size: 12px;
  line-height: 14px;
  color: #606060;
}

.items {
  width: 352px;
  height: 280px;
  margin-top: 24px;
  background: #fff;
  overflow: auto;
}

.items li {
  background: #EEEEEE;
  border-radius: 2px;
  width: 100%;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 16px;
  margin-bottom: 8px;
  box-sizing: border-box;
}

.items li p {
  font-size: 14px;
  line-height: 16px;
  color: #606060;
}


@keyframes slidein {
  from {
    margin-top: 100%;
    width: 300%
  }

  to {
    margin-top: 0%;
    width: 100%;
  }
}

@keyframes slideout {
  from {
    margin-top: 0%;
    width: 300%
  }

  to {
    margin-top: 100%;
    width: 100%;
  }
}


/* ============ Responsive ============ */
@media only screen and (max-width: 768px) {
  .to-do {
    width: 90%;
    height: 400px;
    padding: 24px;
  }

  .items-vazio {
    width: 100%;
  }

  .input .text {
    width: 80%;
  }

  .items {
    width: 100%;
  }
}
</style>
