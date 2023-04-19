<template>
  <div class="principal-container">
  <div>
    <CarrosselDeImagens/>
  </div>
    <!-- <ul>
      <li v-for="user in users" :key="user.id">{{ user.name }}</li>
    </ul> -->
  </div>
</template>

<script lang="ts">
import CarrosselDeImagens from '@/components/CarrosselDeImagens.vue';
import { defineComponent, ref, onMounted } from 'vue';

interface User {
  id: number;
  name: string;
}

export default defineComponent({
    name: "UserList",
    setup() {
        const users = ref<User[]>([]);
        onMounted(async () => {
            const response = await fetch("https://api.themoviedb.org/3/movie/4564?api_key=ea50df2fafdaa8c0f5c42dfbb1bd82f9");
            users.value = await response.json();
        });
        console.log(users);
        return { users };
    },
    components: { CarrosselDeImagens }
});

</script>

<style scoped>
.principal-container{
  width: 100%;
  min-height: 100vh;
  height: auto;
  background-color: black;
}
</style>