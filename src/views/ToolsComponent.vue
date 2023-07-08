<template>
    <div class="tools-container">
        <HeaderComponent />
        <div class="tools-content">
            <router-link to="/shortener">
                <div class="tools-items">

                    <h3 class="item">
                        URL Shortener
                    </h3>
                </div>
              
            </router-link>
        <!-- <div>
            <h3>Welcome to URL trimmer. Click the button above to trim <img src="../assets/scissors.jpg" 
                style="width:100px; height:40px;"></h3>
        </div>          -->
            
        </div>
    </div>
</template>

<script lang="ts">

import { defineComponent } from 'vue';
import HeaderComponent from '@/components/HeaderComponent.vue';

export default defineComponent({
    name: 'DashboardComponent',
    components: {
        HeaderComponent,
    },
});
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;

    font-family: 'Open Sans', sans-serif;
}

.tools-container {
    width: 100%;
    height: 100vh;
    background: #16161a;
    /* background: paleturquoise; */
}

.tools-content {
    display: flex;
    flex-direction: row;
    gap: 20px;
    align-items: center;
    justify-content: center;
    max-width: 1200px;
    margin: 0 auto;
    padding: 50px 20px;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.tools-content a {
    text-decoration: none;
}

.tools-items {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    gap: 10px;
    width: 300px;
    height: 150px;

    padding: 0 20px 20px 20px;

    background-color: pink;

    border: 1px solid #010101;
    border-radius: 100px;
}
.item{
    font-size: 50px;
    font: 900;
    font-style: italic;
}
.tools-items h3 {
    color: brown;
}

@media (max-width: 768px) {
    .tools-content {
        flex-direction: column;
    }
}
</style>