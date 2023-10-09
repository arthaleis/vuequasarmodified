<template>
    <div class="q-pa-md" style="max-width: 400px; text-align: center; margin-left: auto; margin-right: auto;">

    <q-form
        @submit="onSubmit"
        @reset="onReset"
        class="q-gutter-md"
    >
        <q-input
        filled
        v-model="name"
            label="Nama Anda"
        hint="Tuliskan Nama Anda"
        :rules="[ val => val && val.length > 0 || 'Please type something']"
        />

        <q-input
        filled
        type="password"
        v-model="password"
            label="Masukkan Password Pengguna"
        :rules="[ val => val && val.length > 0 || 'Please type something']"
        />

        <q-input
        filled
        v-model="kelas"
            label="Input Kelas"
        :rules="[ val => val && val.length > 0 || 'Please type something']"
        />

        


        <q-toggle v-model="accept" label="I accept the license and terms" />

        <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
        </div>
    </q-form>
    </div>

    <div class="q-pa-md q-gutter-sm">
    <q-banner rounded :class="$q.dark.isActive ? 'bg-grey-0' : 'bg-grey-'">
    <template v-slot:avatar>
        <img
        src="../assets/aldo.jpg"
        style="width: auto; height: 400px;margin-left:170px;"
        >
        <img
        src="../assets/emenqui.jpg"
        style="width: auto; height: 400px;margin-left: 15px;"
        >
        <img
        src="../assets/tidursaja.jpg"
        style="width: auto; height: 400px;margin-left: 15px;"
        >
        <img
        src="../assets/videographerganteng.jpg"
        style="width: auto; height: 400px;margin-left: 15px;"
        >
    </template>


    <template v-slot:action>    
    </template>
    </q-banner>
</div>

</template>

<script>
import { useQuasar } from 'quasar'
import { ref } from 'vue'

export default {
    setup () {
    const $q = useQuasar()

    const name = ref(null)
    const age = ref(null)
    const accept = ref(false)

    return {
        name,
        age,
        accept,

        onSubmit () {
        if (accept.value !== true) {
            $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'You need to accept the license and terms first'
            })
        }
        else {
            $q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'Submitted'
            })
        }
        },

        onReset () {
        name.value = null
        age.value = null
        accept.value = false
        }
    }
    }
}
</script>
