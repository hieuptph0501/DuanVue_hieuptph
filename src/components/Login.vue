<!-- <template>
    <Transition name="modal">
    <div v-if="show" class="modal-mask">
        <template v-slot:header>
            <p>Login</p>
        </template>
        <template>
            <label>Email</label>
            <input id="account" type="email" required />
            <label>Password</label>
            <input id="password" type="password" required />
            <span>Remember me</span>
        </template>
        <template v-slot:footer>
            <button @click="LoginAccount">Login</button>
        </template>
    </div>
  </Transition>
</template> -->
<script>
export default {
    props: {
        show: Boolean
    },
    methods: {
        LoginAccount() {
            if (document.getElementById("account").value === "hieuhieu" && document.getElementById("password").value == "hieu123") {
                alert("Login thành công")
            }
            else{
                alert("Mời bạn nhập Account && Password","Thông báo")
            }
            console.log("Login thất bại")
        }
    },
    // data() {
    //     return account = "hieuhieu",
    //         password = "hieu123"
    // }

}
</script>

<template>
  <Transition name="modal">
    <div v-if="show" class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <slot name="header">default header</slot>
            
          </div>
          <div class="modal-body">
            <slot name="body">LTS Account</slot>
            <input id="account" type="password" required />
          </div>
          <div class="modal-footer">
            <slot name="footer">
              LTS Password<input id="password" type="email" required />
            </slot>
            <button
                class="modal-default-button"
                @click="$emit('close')"
              >Cancle</button>
            <button
                class="modal-default-button"
                @click="LoginAccount"
              >Login</button>
          </div>
        </div>
      </div>
    </div>
  </Transition>
</template>

<style>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 300px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

.modal-header h3 {
  margin-top: 0;
  color: #42b983;
}

.modal-body {
  margin: 20px 0;
}

.modal-default-button {
  float: right;
  margin-bottom: 20px;
}

.modal-enter-from {
  opacity: 0;
}

.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>

