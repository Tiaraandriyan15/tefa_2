    <template>
    <div class="container-fluid d-flex justify-content-center align-items-center" style="background-color: #80A1E8;">
            <div class="col-3">
                <div class = "card shadow p-3 rounded-4" style="background-color: #D9D9D9;">
                    <h1 class="text-center">Login MyAdmin</h1>
                    <form @submit.prevent="loginKeApp">
                        <label>email</label>
                        <input v-model="email" type="email"  class="m-4"><br>
                        <label>password</label>
                        <input v-model="password" type="password" class="m-2"><br>                        
                        <div class="d-grid gap-2 d-md-flex justify-content-md-end">
                            <button class="btn btn-primary me-md-2" type="submit">LOGIN</button>
                        </div>
                    </form>
                </div>
            </div>
    </div>
</template>

<script setup>
const email = ref("")
const password = ref("")
const supabase = useSupabaseClient()

async function loginKeApp() {
    const { data, error } = await supabase.auth.signInWithPassword({
        email: email.value,
        password: password.value,
    })
    if(data) navigateTo('/')

}

</script>





<style setup>
    .container-fluid{
        height: 100vh;
    }

    .card{
        height: 300px;
    }
</style>

<script scope>
    definePageMeta({
        layout: 'loginPage'
    })
</script>
