<template>
  <div>
    <van-cell title="用户名" is-link to="/user/edit" :value="user.username"
              @click="toEdit('username','昵称',user.username)"></van-cell>
    <van-cell title="用户账号" is-link to="/user/edit" :value="user.userAccount"   @click="toEdit('userAccount','用户账号',user.userAccount)"></van-cell>
    <van-cell title="头像" is-link to="/user/edit">
      <img :src="user.avatarUrl" alt="头像" width="20"/>
    </van-cell>
    <van-cell title="性别" is-link to="/user/edit" :value="user.gender"  @click="toEdit('gender','性别',user.gender)"></van-cell>
    <van-cell title="电话号码" is-link to="/user/edit" :value="user.phone"  @click="toEdit('phone','电话号码',user.phone)"></van-cell>
    <van-cell title="电子邮件" is-link to="/user/edit" :value="user.email"  @click="toEdit('email','电子邮件',user.email)"></van-cell>
    <van-cell title="用户状态" is-link to="/user/edit" :value="user.userStatus"  @click="toEdit('userStatus','用户状态',user.userStatus)"></van-cell>
    <van-cell title="用户角色" is-link to="/user/edit" :value="user.userRole"  @click="toEdit('username','用户角色',user.userRole)"></van-cell>
    <van-cell title="星球编号" is-link to="/user/edit" :value="user.plantCode"  @click="toEdit('plantCode','星球编号',user.plantCode)"></van-cell>
    <van-cell title="创建时间" is-link to="/user/edit" :value="user.createTime"  @click="toEdit('createTime','创建时间',user.createTime)"></van-cell>
    <van-cell title="标签" is-link to="/user/edit">
<!--      <span v-for="tag in user.tags" :key="tag" :value="tag"></span>-->
    </van-cell>
  </div>
</template>
<script setup lang="ts">
import {useRouter} from "vue-router";
import {onMounted} from "vue";
import myAxios from "../plugins/axios.ts";
import {showToast} from "vant";
const router=useRouter()
const user = {
  id: 1,
  username : '罗汉',
  userAccount: "doglh",
  avatarUrl: "https://lhwaimai.oss-cn-beijing.aliyuncs.com/logo/logo.jpg",
  gender: 1,
  phone: 123,
  email: 123,
  userStatus: 0,
  userRole: 1,
  plantCode: 1234,
  createTime: Date.now(),
  tags:["java","c++","Python"],
}
//跳转到编辑页
const toEdit=(ediKey: string,editName: string,currentValue: string)=>{
    router.push({
      path:'/user/edit',
      query:{
        ediKey,
        editName,
        currentValue,
      },
    })
}
// onMounted(async () => {
//   const userListData = await myAxios.get('/user/search/tags', {
//     params: {
//       tagsNameList: tags
//     },
//     paramsSerializer: function (params) {
//       return qs.stringify(params, {indices: false});
//     },
//   }).then(function (res) {
//     showToast('请求成功');
//     return res.data?res.data:null;
//   }).catch(function (err) {
//     console.log("err", err)
//   })
//   console.log("userListData",userListData)
//   if (userListData) {
//     userListData.forEach(user=>{
//       if (user.tags){
//         user.tags=JSON.parse(user.tags)
//       }
//     })
//     userList.value = userListData;
//   }
// })
</script>
<style scoped>

</style>