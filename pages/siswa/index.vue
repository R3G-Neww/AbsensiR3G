<template>
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-12">
          <h2 class="text-center my-4">RIWAYAT ABSENSI</h2>
          <div class="my-3">
            <input v-model="keyword" type="search" class="form-control rounded-5" placeholder="Cari...."/> 
          </div>
          <div class="my-3 text-muted">
          menampilkan {{ visitors.length }} dari {{ visitors.length }}
        </div>
          <table class="table">
            <thead>
              <tr>
                <td>#</td>
                <td>nama</td>
                <td>keterangan</td>
                <td>alasan</td>
                <td>waktu</td>
              </tr>   
            </thead>  
            <tbody>
              <tr v-for="(visitor, i) in visitors" :key="i">
                <td>{{ i + 1 }}</td>
              <td>{{ visitor.siswa.nama }}</td>
              <td>{{ visitor.keterangan.nama }}</td>
              <td>{{ visitor.alasan }}</td>
              <td>{{ visitor.waktu }}</td>
            </tr>
            </tbody>
          </table>
        </div>  
      </div>
    </div> 
    <Nuxt-Link to="/home"> 
                 <button type="submit" class="btn btn-secondary btm-lg rounded-5" style="margin-left: 82%;" >BACK</button>
                 </Nuxt-Link>
  </template>
  
  <script setup>
  const supabase = useSupabaseClient ()
  const visitors = ref([])


  const getSiswa = async () => {
    const { data, error } = await supabase.from('form_guru').select('*, keterangan(*), siswa(*)')
    if(data) visitors.value =data
    }
  
    onMounted(() => {
      
      getSiswa()
    })
  </script>