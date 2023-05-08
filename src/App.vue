<script>
export default {
  methods: {
    isPhone(value) {
      if (!value) {
        return '手機為必填'
      }
      const phoneNumber = /^(09)[0-9]{8}$/
      return phoneNumber.test(value) ? true : '要輸入09開頭的手機號碼喔'
    }
  }
}
</script>

<template>
  <VForm class="w-30 mx-auto mt-50" v-slot="{ meta }" @submit="onSubmit">
    <div class="mb-3">
      <label for="name" class="form-label">姓名</label>
      <VField
        name="name"
        :rules="{ max: 10, required, min: 2 }"
        as="input"
        label="姓名"
        type="text"
        class="form-control"
        id="name"
      />
      <ErrorMessage name="name" />
    </div>
    <div class="mb-3">
      <label for="exampleInputEmail1" class="form-label">電子信箱</label>
      <VField
        name="email"
        rules="required|email"
        as="input"
        label="電子信箱"
        type="email"
        class="form-control"
        id="exampleInputEmail1"
      />
      <ErrorMessage name="email" />
    </div>
    <div class="mb-3">
      <label for="mail" class="form-label">寄送方式</label>
      <VField
        name="mail"
        rules="required"
        as="select"
        label="寄送方式"
        type="email"
        class="form-control"
        id="mail"
      >
        <option value="">預設(請選擇)</option>
        <option value="丟過去">丟過去</option>
        <option value="拿過去">拿過去</option>
        <option value="滾過去">滾過去</option>
      </VField>
      <ErrorMessage name="mail" />
    </div>
    <div class="mb-3">
      <label for="phone" class="form-label">手機號碼</label>
      <VField
        name="phone"
        :rules="isPhone"
        as="input"
        label="手機號碼"
        type="tel"
        class="form-control"
        id="phone"
      />
      <ErrorMessage name="phone" />
    </div>
    <div class="mb-3">
      <label for="description" class="form-label">備註</label>
      <VField
        name="description"
        :rules="{ max: 100, required, min: 5 }"
        as="textarea"
        label="備註"
        type="text"
        class="form-control"
        id="description"
      />
      <ErrorMessage name="description" />
    </div>

    <button type="submit" :disabled="!meta.valid" class="btn btn-primary">送出表單</button>
  </VForm>
</template>

<style scoped>
.w-30 {
  width: 30%;
}
.mx-auto {
  margin: 0 auto;
}
mt-50 {
  margin-top: 50px;
}
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
