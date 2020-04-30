<template>
  <div class="commintedit">
    <p class="usertiitle">
      评论管理
      <i>/</i>编辑评论
    </p>
    <div class="usereditfrom">
      <div class="loginContant">
        <i-form class="loginFrom" ref="formInline" :model="formInline" :rules="ruleInline" inline>
          <div class="info_item">
            <label for>评论人：</label>
            <Form-item prop="name">
              <i-input type="text" v-model="formInline.name" style="width: 200px;"></i-input>
            </Form-item>
          </div>
          <div class="info_item">
            <label for>评论歌曲：</label>
            <Form-item prop="tel">
              <i-input type="text" style="width:200px;" v-model="formInline.tel"></i-input>
            </Form-item>
          </div>
          <div class="info_item">
            <label for>评论留言：</label>
            <Form-item prop="tel">
              <i-input type="text" style="width:200px;" v-model="formInline.tel"></i-input>
            </Form-item>
          </div>
          <div class="info_item">
            <p class="surebtn" @click="handleSubmit('formInline')">确定</p>
            <p class="cancelbtn" @click="cancel">取消</p>
          </div>
        </i-form>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      formInline: {
        name: "",
        tel: ""
      },
      ruleInline: {
        name: [{ required: true, message: "请填写用户名", trigger: "blur" }],
        tel: [
          { required: true, message: "请填写密码", trigger: "blur" },
          {
            type: "string",
            min: 6,
            message: "密码长度不能小于11位",
            trigger: "blur"
          }
        ]
      }
    };
  },
  methods: {
    cancel() {
      this.$router.push({
        path: "/comment"
      });
    },
    handleSubmit(name) {
      this.$refs[name].validate(valid => {
        if (valid) {
          this.getUser();
        }
      });
    },
    getUser() {
      this.axios
        .get("/admin/member", {
          params: {}
        })
        .then(resp => {
          if (resp.status == 200) {
            console.log(resp);
          }
        });
    }
  }
};
</script>

<style lang="less">
.commintedit {
  .usertiitle {
    font-size: 24px;
    font-weight: 500;
    margin-bottom: 20px;
    color: rgba(0, 0, 0, 1);
    i {
      margin: 0 10px;
    }
  }
  .usereditfrom {
    .info_item {
      display: flex;
      label {
        margin-top: 8px;
      }
    }
    .surebtn,
    .cancelbtn {
      width: 100px;
      height: 40px;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-right: 20px;
      cursor: pointer;
      color: #fff;
      border-radius: 5px;
    }
    .surebtn {
      background-color: skyblue;
    }
    .cancelbtn {
      background-color: #999;
    }
    .surebtn:hover {
      opacity: 0.8;
    }
    .cancelbtn:hover {
      opacity: 0.8;
    }
  }
}
</style>