<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12 d-flex justify-content-center">
        <form @submit.prevent="login">
          <div class="col-4 p-5">
            <div class="card-body">
              <h2 class="d-flex justify-content-center p-4 fw-bold fs-2">Selamat Datang Di Kelas XII PPLG 2</h2>
              <div class="mb-3">
                <label for="exampleFormControlInput1" class="form-label fw-bold">Email:</label>
                <input v-model="email" type="email" class="form-control" id="exampleFormControlInput1">
              </div>
              <div class="mb-3">
                <label for="exampleFormControlInput1" class="form-label fw-bold">Password:</label>
                <input v-model="password" type="password" class="form-control" id="exampleFormControlInput1">
              </div>
              <button type="submit" style="width: 100px;" class="rounded-3 m-2">login</button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card-body {

  height: 450px;
  color: black;
  width: 300px;
  box-shadow: 1px 1px 10px;
  border-radius: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
<script setup>
const supabase = useSupabaseClient()

const email = ref('')
const password = ref('')

async function login() {
  const { data, error } = await supabase.auth.signInWithPassword({
    email: email.value,
    password: password.value,
  })


  if (!error) {
    navigateTo('/home')
  } else {
    alert("Passwordnya lupa apa lupa nich?!?!?!?!?")
  }
}

</script>