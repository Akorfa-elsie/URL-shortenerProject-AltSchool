<template>
    <div class="url-container">
        <HeaderComponent />
        <div class="url-shortener-form">
            <div class="url-string-bits">
                <div class="url-div">
                    <input type="text" v-model="url" @keyup.enter="getData()" id="orig-url" placeholder="Place URL here...">
                </div>
            </div>
            <div >
                <button @click="getData()" class="trim-url">
                    Trim URL
                    <!-- <svg width="25" height="25" viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M9.45887 8.31619C9.43991 8.5416 9.11191 8.59859 9.00642 8.39481L8.43834 7.29767C8.4016 7.22658 8.32675 7.17907 8.24209 7.17292L6.93485 7.07809C6.692 7.06049 6.63061 6.75601 6.85016 6.65807L8.03196 6.13074C8.10849 6.09658 8.15977 6.02715 8.16632 5.94854L8.26849 4.73494C8.28745 4.50953 8.61545 4.45254 8.72095 4.65632L9.28902 5.75346C9.32576 5.82455 9.40052 5.87207 9.48527 5.87821L10.7925 5.97303C11.0354 5.99064 11.0967 6.29511 10.8772 6.39306L9.6954 6.92039C9.61878 6.95457 9.56759 7.02397 9.56104 7.10259L9.45887 8.31619Z"
                            fill="white" />
                        <path
                            d="M5.70605 9.1442C5.6744 9.25336 5.50755 9.25336 5.4759 9.1442L5.30543 8.55649C5.29442 8.51841 5.26233 8.48867 5.22134 8.47842L4.58827 8.32018C4.47067 8.29079 4.47067 8.13591 4.58827 8.10652L5.22134 7.94828C5.26233 7.93802 5.29442 7.90828 5.30543 7.87021L5.4759 7.28249C5.50755 7.17333 5.6744 7.17333 5.70605 7.28249L5.87652 7.87021C5.88754 7.90828 5.91957 7.93802 5.96061 7.94828L6.59368 8.10652C6.71129 8.13591 6.71129 8.29079 6.59368 8.32018L5.96061 8.47842C5.91957 8.48867 5.88754 8.51841 5.87652 8.55649L5.70605 9.1442Z"
                            fill="white" />
                        <path
                            d="M7.88769 12.5199C7.85604 12.6291 7.68919 12.6291 7.65754 12.5199L7.48707 11.9322C7.47606 11.8941 7.44398 11.8644 7.40298 11.8541L6.76991 11.6959C6.65231 11.6665 6.65231 11.5116 6.76991 11.4822L7.40298 11.324C7.44398 11.3138 7.47606 11.284 7.48707 11.2459L7.65754 10.6582C7.68919 10.5491 7.85604 10.5491 7.88769 10.6582L8.05816 11.2459C8.06918 11.284 8.10121 11.3138 8.14226 11.324L8.77532 11.4822C8.89293 11.5116 8.89293 11.6665 8.77532 11.6959L8.14226 11.8541C8.10121 11.8644 8.06918 11.8941 8.05816 11.9322L7.88769 12.5199Z"
                            fill="white" />
                        <path
                            d="M6.03133 11.1969C6.01023 11.2697 5.899 11.2697 5.87789 11.1969L5.76425 10.8051C5.75691 10.7797 5.73552 10.7599 5.70819 10.753L5.28614 10.6475C5.20774 10.6279 5.20774 10.5247 5.28614 10.5051L5.70819 10.3996C5.73552 10.3928 5.75691 10.3729 5.76425 10.3476L5.87789 9.95574C5.899 9.88297 6.01023 9.88297 6.03133 9.95574L6.14498 10.3476C6.15232 10.3729 6.17367 10.3928 6.20104 10.3996L6.62308 10.5051C6.70149 10.5247 6.70149 10.6279 6.62308 10.6475L6.20104 10.753C6.17367 10.7599 6.15232 10.7797 6.14498 10.8051L6.03133 11.1969Z"
                            fill="white" />
                        <path
                            d="M11.1222 9.84654C11.101 9.91932 10.9898 9.91932 10.9687 9.84654L10.8551 9.45473C10.8477 9.42935 10.8263 9.40952 10.799 9.40268L10.377 9.29719C10.2986 9.2776 10.2986 9.17434 10.377 9.15475L10.799 9.04926C10.8263 9.04242 10.8477 9.0226 10.8551 8.99721L10.9687 8.6054C10.9898 8.53263 11.101 8.53263 11.1222 8.6054L11.2358 8.99721C11.2431 9.0226 11.2645 9.04242 11.2919 9.04926L11.7139 9.15475C11.7923 9.17434 11.7923 9.2776 11.7139 9.29719L11.2919 9.40268C11.2645 9.40952 11.2431 9.42935 11.2358 9.45473L11.1222 9.84654Z"
                            fill="white" />
                        <path
                            d="M18.3182 18.0032L17.5909 18.6783M8.15777 9.0424L19.9624 19.0878C20.2555 19.3372 20.2654 19.7631 19.9843 20.024V20.024C19.7043 20.284 19.2496 20.2779 18.9805 20.0081C14.9047 15.9232 7.72842 8.70759 8.15777 9.0424Z"
                            stroke="white" />
                    </svg> -->
                </button>
                
            </div>
            <div class="output">
                <h3 class="history">History of Shortened links:</h3>
                <ul>
                    <li v-for="(link, i) in links" :key="i" class="link-item">
                        <span class="link-and-copy">
                            <a :href="link" target="_blank" rel="noreferrer">
                                <p>{{ link }}</p>
                            </a>
                        </span>
                        <button @click="copyLink(link)" class="copy-btn">Copy</button>
                    </li>
                </ul>
            </div>
            <router-link to="/"><button className='counter-btn'>
                 Back to Homepage
                </button></router-link>
        </div>
    </div>
</template>


<script lang="ts">
import { defineComponent } from 'vue';
import HeaderComponent from '@/components/HeaderComponent.vue';
import useClipboard from 'vue-clipboard3';

export default defineComponent({
    name: 'URLComponent',
    components: {
        HeaderComponent
    },
    setup() {
        const { toClipboard } = useClipboard();
        return { toClipboard };
    },
    data() {
        return {
            url: '',
            link: '',
            links: [] as Array<string>,
        }
    },
    methods: {
        async getData() {
            try {
                const response = await fetch('https://api.shrtco.de/v2/shorten?url=' + this.url);
                const data = await response.json();
                this.links.push(data.result.full_short_link);
                this.url = '';
            } catch (error) {
                console.log(error);
            }
        },
        async copyLink(link: string) {
            try {
                await this.toClipboard(link);
                alert('Link copied to clipboard');
            } catch (error) {
                console.log(error);
            }
        }
    },


    created() {
        this.getData();
    }
});
</script>


<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;

    font-family: 'Open Sans', sans-serif;
}

.url-container {
    width: 100%;
    height: 100vh;
    background: #16161a;
    
}

.link-item {
    list-style-type: none;
    text-align: left;
    padding: 5px;
}

li.link-item {
    border: 2px solid #010101;
    background: pink;
    border-radius: 10px;
    padding: 5px 10px;
    margin: 10px 0;
    width: 100%;
}

.copy-btn {
    padding: 10px;
    border-radius: 25px;
    color: brown;

    background: pink;
    border: none;

    margin: 10px 0;
    cursor: pointer;
}

.redirect-button {
    padding: 12px 24px;
    width: 392px;
    height: 48px;
    font-size: 15px;

    /* Primary/400 */

    color: brown;

    background: pink;
    border-radius: 100px;
    border: none;

    cursor: pointer;
}

.url-shortener-form {
    max-width: 1200px;
    margin: 0 auto;
    padding: 50px 20px;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);

    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 24px;

    padding: 50px 24px;


    color: brown;
    background: #16161a;
    border: 3px solid #010101;
    border-radius: 12px;
}

.history{
    color: #afafaf;
}
.url-string-bits {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 0px;
    gap: 24px;

    width: 392px;

    flex: none;
    order: 0;
    flex-grow: 0;
}

.buttons-legal-bits {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 0px;
    gap: 12px;

    width: 392px;
    height: 120px;

    flex: none;
    order: 1;
    flex-grow: 0;
}

.output {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 0px;
    gap: 12px;
    margin-top: 0px;

    width: 392px;

    flex: none;
    order: 2;
    flex-grow: 0;
}

.trim-url {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 12px 24px;
    gap: 10px;

    width: 392px;
    height: 48px;

    /* Primary/400 */

    color: brown;

    background: pink;
    border-radius: 100px;
    border: none;
    cursor: pointer;

    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 0;
}


.counter-btn {
    background-color: pink;
    color: brown;
    margin: 5px;
    padding: 10px 15px;
    border: none;
    border-radius: 10px;
}

.url-div {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    /* padding: 8px 12px; */
    gap: 10px;

    width: 100%;
    height: 55px;

}

#orig-url {
    width: 100%;
    padding: 12px 12px;
    border: 1px solid pink;
    border-radius: 12px;

    color: #94a1b2;

    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 0;
}

#orig-url::placeholder {
    /* Primary/200 */

    color: #94a1b2;
}

#orig-url:focus {
    outline: 1px solid pink;
}

@media (max-width: 600px) {
    .url-shortener-form {
        width: 90%;
        padding: 50px 24px;
    }

    .url-string-bits {
        width: 100%;
    }

    .buttons-legal-bits {
        width: 100%;
    }

    .result {
        width: 100%;
    }

    .trim-url {
        width: 100%;
    }

    .legal-bits {
        width: 100%;
    }

    .url-div {
        width: 100%;
    }

    #orig-url {
        width: 100%;
    }
}
</style>