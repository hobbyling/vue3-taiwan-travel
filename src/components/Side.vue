<template>
  <div class="side">
    <img src="../assets/logo.svg" alt="Travel Logo" class="logo">
    <div class="form">
      <div class="form__item select">
        <span>目的地</span>
        <Arrow class="form__item__icon" />
      </div>
      <div class="form__item search">
        <input type="text" placeholder="關鍵字">
        <Search class="form__item__icon" />
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
      }]
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

  // 表單
  .form {
    width: calc(100% - 48px);
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
      width: calc(100% - 48px);

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
</style>
