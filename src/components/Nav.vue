<template>
     <nav class="w-full z-50 bg-blue-50 dark:bg-gray-800" style="position: fixed; top:0%;width: 100%">
            <div class="container mx-auto py-5  xs:px-2 sm:px-2 flex items-center justify-between ">

                <div class="nav__logo__links flex items-center">
                    <router-link :to="{name: 'home'}">


                        <div class=" logo flex items-center cursor-pointer">
                                <div class=" h-10  w-10 bg-blue-600 rounded-full flex items-center justify-center mr-2">
                                    <span class="h-3  w-3 bg-white "></span>
                                </div>
                                <h4 class=" text-gray-800 dark:text-blue-100 font-bold">ATLAS</h4>
                        </div>
                    </router-link>
                        <div class="links flex items-center ml-10 xs:hidden lg:flex">
                    
                            <span class="flex items-center mx-3">
                                <!-- <Link href={'/blog'}>Blog</Link> -->
                                <router-link :to="{name: 'blog'}">
                                   <span class="dark:text-gray-100">Blog</span>
                                </router-link>
                            </span>
                            <span class="flex items-center mx-3">
                            <router-link :to="{name: 'shop'}">
                                <span class="dark:text-gray-100">Shop</span>
                                </router-link>
                            </span>
                        </div>
                </div>

                <div class="nav_right_links  items-center xs:hidden  sm:hidden lg:flex ">
                    <div class="searchbox flex items-center border rounded overflow-hidden px-2 mr-8 dark:border-gray-400">
                        <i class="bi bi-search text-gray-400 dark:text-gray-500"></i>

                        
                        <input type="text" placeholder="Search..." class=" border-0 outline-none p-2 bg-transparent dark:text-gray-100"/>
                    </div>
                    <div class="links flex items-center">
                       
                       <router-link :to='{name: "cart"}'>

                        <a class="mx-3 cursor-pointer relative">
                            <i class="bi bi-cart text-gray-500 dark:text-gray-400 text-lg dark:hover:text-gray-200"></i>
                            <span class=" absolute bottom-3 left-3 text-red-500">{{cart}}</span>
                        </a>
                       </router-link>
                        <router-link :to='{name: "profile"}'>

                        <a class="mx-3 cursor-pointer">
                            <i class="bi bi-person text-gray-500 dark:text-gray-400 text-lg dark:hover:text-gray-200"></i>

                            
                        </a>
                        </router-link>
                       
                        <a class="mx-3 cursor-pointer">
                            
                            <i class="bi bi-moon-stars-fill text-blue-500" v-if="theme=='light'" @click="addDarkTheme"></i>
                            <i class="bi bi-brightness-high text-yellow-300 text-lg" v-else @click="addLightTheme"></i>


                        </a>
                    </div>
                </div>
                <div class=" cursor-pointer lg:hidden flex items-center">
                    <router-link to="/cart">

                   <div class="relative cursor-pointer">
                        <i class="bi bi-cart sm:text-lg dark:text-gray-200"></i>
                     
                       <span class=" absolute bottom-1 left-3 text-red-500">{{cart}}</span>
                   </div>
                    </router-link>
                    <a class="mx-3 cursor-pointer">
                             <i class="bi bi-moon-stars-fill text-blue-500" v-if="theme=='light'" @click="addDarkTheme"></i>
                            <i class="bi bi-brightness-high text-yellow-300 text-lg" v-else @click="addLightTheme"></i>
                              
                        </a>
                        <i class="bi bi-list sm:text-xl cursor-pointer dark:text-gray-200" @click="openModal"></i>

                   
                </div>
            </div>
        </nav>
</template>
<script>
import { mapGetters } from "vuex"
export default {
    name: "Nav",
    
    computed:{
        ...mapGetters({cart: 'totalCartItems',theme: 'getCurrentTheme'})
        // cart(){
        //     console.log(this.$store.state.carts.length)
        //     return this.$store.state.carts.length
        // }
    },
    methods:{
        openModal(){
            this.$store.commit('openModal')
        },
        addDarkTheme(){
            this.$store.commit('addDarkTheme')
            // console.log(document.querySelector("html").classList.add("dark"))
        },
        addLightTheme(){
            this.$store.commit('addLightTheme')
        }
    }
}
</script>
<style lang="">
    
</style>