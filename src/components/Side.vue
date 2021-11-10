<template>
  <div class="side">
    <img src="../assets/logo.svg" alt="Travel Logo" class="logo">
    <div class="form">
      <div class="form__item search">
        <input type="text" placeholder="關鍵字">
        <Search class="form__item__icon" />
      </div>
    </div>
    <div class="form">
      <h2>目的地</h2>
      <div class="form__item select">
        <span>目的地</span>
        <Arrow class="form__item__icon" />
      </div>
      <!-- 下拉選單 -->
      <div class="dropdown">
        <div class="region" v-for="item in region" :key="item.code">
          <div class="title">{{item.name}}</div>
          <div class="btns">
            <div v-for="area in item.list" :key="area.code" class="btn">
              {{area.name}}
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="theme">
      <h2>精選主題</h2>
      <div class="theme__items">
        <div class="theme__items__item" v-for="(item, key) in theme" :key="'theme'+key">
          <img :src="item.image" :alt="item.name">
          <span class="theme__items__item__name">{{ item.name }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Arrow from '@/components/ArrowIcon.vue'
import Search from '@/components/SearchIcon.vue'
import regionJson from '@/utils/region'
export default {
  name: 'Side',
  components: {
    Arrow,
    Search
  },
  data () {
    return {
      theme: [{
        name: '歷史文化',
        image: require('@/assets/icon/class1.svg')
      },
      {
        name: '戶外踏青',
        image: require('@/assets/icon/class2.svg')
      },
      {
        name: '宗教巡禮',
        image: require('@/assets/icon/class3.svg')
      },
      {
        name: '親子活動',
        image: require('@/assets/icon/class4.svg')
      },
      {
        name: '風景區',
        image: require('@/assets/icon/class5.svg')
      },
      {
        name: '美食品嚐',
        image: require('@/assets/icon/class6.svg')
      },
      {
        name: '住宿推薦',
        image: require('@/assets/icon/class7.svg')
      },
      {
        name: '觀光活動',
        image: require('@/assets/icon/class8.svg')
      }],
      region: regionJson,
      form: {
        area: ''
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.side {
  padding: 40px 24px;
  display: flex;
  flex-direction: column;

  // Logo
  .logo {
    width: 116.5px;
    height: 47px;
    margin-bottom: 24px;
  }

  // 標題
  h2 {
      color: #222;
      font-size: 18px;
      font-weight: bold;
      line-height: 24px;
      letter-spacing: 0.15px;
      text-align: left;
      margin-bottom: 24px;
      &::before{
        display: block;
        content: '';
        border-top: 1px solid rgba(0,0,0,.08);
        margin-bottom: 24px;
      }
    }

  // 表單
  .form {
    width: 100%;
    position: relative;
    &__item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 8px 12px;
      background: #FAFAFA;
      border-radius: 8px;
      border: 1px solid rgba(0,0,0,.08);
      text-align: left;
      font-size: 18px;
      line-height: 27px;

      &:last-child {
        margin: 24px 0;
      }
    }

    input {
      border: none;
      font-size: 18px;
      background: #FAFAFA;
    }
  }

  .form__item__icon:hover {
    cursor: pointer;
  }

  // 主題
  .theme {
    &__items {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      &__item {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 8px 37.5px;
        margin-bottom: 12px;
        cursor: pointer;

        img {
          width: 70px;
          height: 70px;
        }

        &__name {
          color: #222;
          font-size: 16px;
          line-height: 24px;
        }
      }
    }
  }

  .theme__items__item:hover {
    .theme__items__item__name {
      color: #3FB195;
    }
  }
}

// 目的地下拉選單
.dropdown {
  position: absolute;
  width: calc(100% - 30px);
  height: 400px;
  overflow-y: scroll;
  margin: 0 auto;
  padding: 20px 15px;
  background: #fff;
  box-shadow: 0px 14px 24px rgba(0, 0, 0, 0.12);

  .region{
    margin-bottom: 20px;
    .title {
      text-align: left;
      font-size: 18px;
      font-weight: bold;
      margin-bottom: 10px;
    }

    .btns {
      display: flex;
      align-items: center;
      justify-content: flex-start;
      flex-wrap: wrap;

      .btn {
        display: flex;
        align-items: center;
        justify-content: center;
        border: 1px solid #3FB195;
        box-sizing: border-box;
        border-radius: 8px;
        background: #FFFFFF;
        width: 75px;
        height: 35px;
        font-size: 18px;
        line-height: 27px;
        letter-spacing: 0.15px;
        margin-bottom: 12px;
        cursor: pointer;

        &:nth-child(3n) {
          margin-left: 18px;
        }

        &:nth-child(3n+2) {
          margin-left: 18px;
        }

        &:hover {
          background: #3FB195;
          color: #fff;
        }
      }
    }
  }
}

//捲軸底色
.dropdown::-webkit-scrollbar-track {
  -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  background-color: #fff;
}
//捲軸寬度
.dropdown::-webkit-scrollbar {
  width: 6px;
  background-color: #fff;
}
//捲軸本體顏色
.dropdown::-webkit-scrollbar-thumb {
  background-color: #3FB195;
}

</style>
