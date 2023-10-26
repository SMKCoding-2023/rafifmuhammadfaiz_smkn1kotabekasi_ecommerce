import { NuxtLink } from '#build/components';
<template> 
    <header class="w-full border-b border-slate-200 py-6"> 
    <div class="container"> 
    <div class="flex justify-between items-center"> 
    <div> 
    <NuxtLink to="/" class="text-xl font-bold">SMK Coding</NuxtLink> 
    </div> 
    <nav class="flex items-center gap-6"> 
    <NuxtLink to="/" class="text-base">Beranda</NuxtLink>  
    <NuxtLink to="/product" class="text-base">Product</NuxtLink> 
    <NuxtLink to="/cart" class="text-base">Cart</NuxtLink>  
    </nav> 
    </div> 
    </div> 
    </header> 
   </template>