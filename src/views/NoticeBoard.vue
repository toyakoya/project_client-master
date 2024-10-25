<template>
  <div :style="backgroundStyle" class="notice-container">
      <div>
        <span class="notice-content">
          <h1>标题</h1>
          <p>一条消息</p>
        </span>
        <el-divider></el-divider>
        <span class="notice-content">
          <h1>标题</h1>
          <p>一条消息</p>
        </span>
        <el-divider></el-divider>
        <span class="notice-content">
          <h1>标题</h1>
          <p>一条消息</p>
        </span>
        <el-divider></el-divider>
      </div>

  </div>
</template>

<script>
export default {
  name: 'NoticeView',
  computed: {
    backgroundStyle() {
      return {
        backgroundSize: 'cover',
        height: '97vh',
      };
    }
  }
}
</script>

<style scoped>
.notice-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  color: white;
  padding: 0;
  margin: 0;
}

.notice-content {
  background: rgba(0, 0, 0);
  border-radius: 1px;
  //padding: 40px;
  width: 100%;
  text-align: center;
}

.notice-content h1 {
  font-size: 36px;
  font-weight: bold;
  color: black;
}

.notice-content p {
  font-size: 18px;
  color: black;
  margin-top: 20px;
}
</style>