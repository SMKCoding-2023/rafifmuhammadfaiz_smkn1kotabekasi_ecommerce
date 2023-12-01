<script lang="ts" setup>
import { useAuthStore } from "~/stores/auth"
const authStore = useAuthStore();
const isAuthenticated = ref();
const router = useRouter();

isAuthenticated.value = useCookie("access_token").value;

const logout = async () => {
await authStore.logout();
const accessToken = useCookie("access_token");
const refreshToken = useCookie("refresh_token");
accessToken.value = null;
refreshToken.value = null;
setTimeout(() => {
isAuthenticated.value = useCookie("access_token").value;
}, 100);
router.push({
path: "/"
})
}
</script>
<template> 
    <header class="w-full border-b bg-green-600 py-6" color="#00ab59"> 
        <div class="container"> 
        <div class="flex justify-between items-center"> 
        <div> 
            <NuxtLink to="/" class="text-xl font-bold  bg-green-600">RAJA OLSHOP</NuxtLink> 
        </div> 
    <nav class="flex items-center gap-6"> 
    <NuxtLink to="/" class="text-base font-semibold bg-purple-700  hover:bg-blue-600/80">HOME</NuxtLink>  
    <NuxtLink to="/product" class="text-base font-semibold bg-yellow-600 hover:bg-yellow-500/80" >ARTICLE</NuxtLink> 
    <NuxtLink to="/cart" class="text-base font-semibold bg-blue-600 hover:bg-purple-500/80">CART</NuxtLink>  
    <NuxtLink v-if="!isAuthenticated" to="/login" class="text-base bg-blue-600 px-6 py-2 text-white rounded-lg hover:bg-purple-600/80">Login</NuxtLink>
        <div v-else class="text-base cursor-pointer bg-red-600 px-6 py-2 text-white rounded-lg hover:bg-red-700/80" @click="logout">Logout</div>
    </nav> 
    </div> 
    </div> 
    </header> 
   </template>