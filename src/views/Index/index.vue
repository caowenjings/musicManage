<template>
  <div class="welcome">
    <div class="welcomebox">
      <img src="../../assets/hai.png" alt />
      <p>欢迎来到鸹貔音乐！</p>
    </div>
  </div>
</template>
<script>
export default {};
</script>

<style lang="less">
.welcome {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  .welcomebox {
    display: flex;
    justify-content: center;
    align-items: center;
    img {
      width: 180px;
      height: 180px;
      border-radius: 10px;
    }
    p {
      margin-left: 10px;
      font-size: 36px;
      font-family: 'Zurich Bold', sans-serif; 
      font-weight: 400;
      color: rgba(0, 102, 204, 1);
      line-height: 50px;
      letter-spacing: 5px;
    }
  }
}
</style>