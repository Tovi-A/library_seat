<template>
  <div class="login-page">
    <h1>用户登录</h1>

    <!-- 学校选择 -->
    <label for="school">选择学校：</label>
    <select v-model="selectedSchool" @change="changeSchool">
      <option v-for="(school, index) in schools" :key="index" :value="school.id">{{ school.name }}</option>
    </select>

    <!-- 账号输入 -->
    <label for="username">账号：</label>
    <input type="text" v-model="username" />

    <!-- 密码输入 -->
    <label for="password">密码：</label>
    <input type="password" v-model="password" />

    <!-- 登录按钮 -->
    <button @click="login">登录</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedSchool: null,
      username: '',
      password: '',
      schools: [
        { id: 1, name: '学校A', accounts: ['userA1', 'userA2'] },
        { id: 2, name: '学校B', accounts: ['userB1', 'userB2'] },
        // Add more schools as needed
      ]
    };
  },
  methods: {
    changeSchool() {
      // 在这里可以根据选择的学校更新其他相关的数据
    },
    login() {
      // 在这里可以添加登录逻辑，验证账号密码等
      if (this.selectedSchool !== null && this.username !== '' && this.password !== '') {
        const selectedSchoolObj = this.schools.find(school => school.id === this.selectedSchool);
        if (selectedSchoolObj && selectedSchoolObj.accounts.includes(this.username)) {
          // 登录成功的处理，可以跳转页面或执行其他操作
          console.log('登录成功');
        } else {
          console.log('登录失败：无效的账号或密码');
        }
      } else {
        console.log('请填写完整信息');
      }
    }
  }
};
</script>

<style>
/* 在这里可以添加样式 */
.login-page {
  max-width: 400px;
  margin: 0 auto;
}

/* 添加样式以保证文本框在标签后面 */
label {
  display: block;
  margin-bottom: 8px;
}

/* 确保文本框可以输入 */
input {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
  margin-bottom: 12px;
}
</style>
