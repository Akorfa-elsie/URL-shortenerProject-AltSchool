<template>
    <div class="signup-container">
        <HeaderComponent />
        <div class="signup">
            <p class="sign">Sign up with:</p>
            <div class="socials">
                <button @click.prevent="signInWithGoogle" class="social-button">
                    <svg width="20" height="19" viewBox="0 0 20 19" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M19.5556 9.7111C19.5556 9.07776 19.4444 8.33887 19.3333 7.8111H10V11.5055H15.3333C15.1111 12.6667 14.4444 13.6167 13.3333 14.3555V16.7833H16.6667C18.5556 15.0944 19.5556 12.5611 19.5556 9.7111Z"
                            fill="#4285F4" />
                        <path
                            d="M10.0002 19C12.6669 19 15.0002 18.1556 16.6669 16.6778L13.3335 14.3556C12.4447 14.8834 11.3335 15.3056 10.0002 15.3056C7.44466 15.3056 5.22244 13.6167 4.44466 11.4H1.11133V13.7222C2.66688 16.8889 6.11133 19 10.0002 19Z"
                            fill="#34A853" />
                        <path
                            d="M4.44444 11.2944C4.22222 10.7667 4.11111 10.1333 4.11111 9.49999C4.11111 8.86666 4.22222 8.23333 4.44444 7.70555V5.27777H1.11111C0.444444 6.54444 0 8.02222 0 9.49999C0 10.9778 0.333333 12.4555 1.11111 13.7222L4.44444 11.2944Z"
                            fill="#FBBC05" />
                        <path
                            d="M10.0002 3.8C11.4447 3.8 12.778 4.32778 13.778 5.17222L16.6669 2.42778C15.0002 0.95 12.6669 0 10.0002 0C6.11133 0 2.66688 2.11111 1.11133 5.27778L4.44466 7.70556C5.22244 5.48889 7.44466 3.8 10.0002 3.8Z"
                            fill="#EA4335" />
                    </svg>
                    Google
                </button>
            </div>
            <div class="separator">
                <svg width="203" height="2" viewBox="0 0 203 2" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M1.00977 1H201.51" stroke="#A0B1C0" stroke-linecap="round" />
                </svg>
                <span class="separator-text">Or</span>
                <svg width="203" height="2" viewBox="0 0 203 2" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M1.00977 1H201.51" stroke="#A0B1C0" stroke-linecap="round" />
                </svg>
            </div>
            <div class="signup-form">
                <form name="signUpForm">
                    <input type="email" v-model="email" id="email" placeholder="Email" required>
                    <input type="password" v-model="password" id="password" pattern="(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{6,}"
                        placeholder="Password" required>
                    <!-- <span class="password-reqs"></span> -->
                    <input @click.prevent="register" type="submit" value="Sign up with Email ">
                </form>
                <div class="log-in">
                    <p class="sign">Already have an account?</p>
                    <span>
                        <router-link to="/login">Log in</router-link>
                    </span>
                </div>
                
            </div>
        </div>
    </div>
</template>


<script lang="ts">
import { defineComponent, ref } from 'vue';
import {
    getAuth,
    createUserWithEmailAndPassword,
    GoogleAuthProvider,
    signInWithPopup,
} from 'firebase/auth';
import router from '../router'
import HeaderComponent from '@/components/HeaderComponent.vue';

export default defineComponent({
    name: 'RegisterComponent',
    components: {
        HeaderComponent,
    },
    setup() {
        const email = ref('');
        const password = ref('');

        // const checkPassword = () => {

        // } 

        const register = () => {

            const auth = getAuth();
            createUserWithEmailAndPassword(auth, email.value, password.value)
                .then((data) => {
                    router.push('/');
                })
                .catch((error) => {
                    switch (error.message) {
                        case "auth/email-already-exists":
                            alert("This user already exists")
                            break;
                        case "auth/invalid-email":
                            alert("Please enter a valid email address.")
                            break;
                        case "auth/invalid-password":
                            alert("Invalid password")
                            break;
                        default:
                            alert("Something went wrong.")
                            break;
                    }
                });


        }

        const signInWithGoogle = () => {
            const provider = new GoogleAuthProvider();
            signInWithPopup(getAuth(), provider)
                .then((result) => {
                    router.push('/analytics')
                })
                .catch((error) => {
                    alert(error.message)
                })
        }
        return {
            email,
            password,
            register,
            signInWithGoogle,
        }
    },
})
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;

    font-family: 'Open Sans', sans-serif;
}

.signup-container {
    width: 100%;
    height: 100vh;
    /* background: paleturquoise; */
    background: #16161a;
}

.signup {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    padding: 0px;
    gap: 16px;

    max-width: 1200px;
    margin: 0 auto;
    padding: 50px 20px;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.sign{
    color: #afafaf;
}

.socials {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    padding: 0px;
    gap: 24px;

    width: 242px;
    height: 40px;
    margin: auto;


    /* Inside auto layout */

    flex: none;
    flex-grow: 0;
}

.social-button {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 40px;

    /* Primary/400 */

    background: pink;
    border-radius: 3px;
    border-style: none;
    color: brown;
    text-align: center;

    /* Inside auto layout */

    flex: none;
    flex-grow: 0;
}

.separator {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    padding: 0px;

    width: 100%;
    height: 26px;
    margin: auto;


    /* Inside auto layout */

    flex: none;
    flex-grow: 0;
}

.separator-text {
    padding: 1px 19.98px 1px 20px;
    font-size: 16px;
    line-height: 24px;
    color: #afafaf;
}

.signup-form {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0px;

    width: 70%;
    margin: auto;

    flex: none;
    flex-grow: 0;
}

form {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    gap: 16px;
    border-radius: 4px;
    box-sizing: border-box;
}

input[type='text'],
input[type='password'],
input[type='email'] {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 2px solid pink;
    border-radius: 10px;

    font-size: 16px;
    line-height: 24px;
}

input:invalid {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 2px solid black;
}

input[type='submit'] {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 12px 24px;
    margin: 8px 0;
    gap: 10px;
    width: 100%;

    background: pink;
    border-radius: 100px;
    border: 2px solid oink;
    cursor: pointer;

    font-size: 14px;
    line-height: 12px;
    color: brown;
}

.password-reqs {
    font-size: 12px;
    line-height: 20px;
    color: #94a1b2;
    /* or 143% */

    display: flex;
    align-items: center;
}

.log-in {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 0px;
    gap: 5px;

    width: 100%;
}

.log-in a {
    text-decoration: none;
    color: pink;
}

.terms {
    width: 100%;
    margin: auto;

    font-size: 12px;
    line-height: 18px;
    

    color: #94a1b2;

}

.grey {
    color: rgba(92, 111, 127, 1);
}

button:hover {
    cursor: pointer;
}

@media (max-width: 600px) {
    .signup {
        width: 90%;
    }

    .signup-form {
        width: 100%;
    }
}

@media (max-width: 768px) {
    .signup-form {
        width: 100%;
    }
}

@media (max-width: 1024px) {
    .signup-form {
        width: 100%;
    }
}
</style>