<script setup>
import Container from "./Container.vue"
import { ref } from "vue"
import emailjs from 'emailjs-com';

const { VITE_EMAIL_SERVICE_ID, VITE_EMAIL_TEMPLATE_ID, VITE_EMAIL_KEY } = import.meta.env;

const emailForm = ref(null);
const name = ref("");
const email = ref("");
const message = ref("");
const errorMsg = ref("");
const successMsg = ref("");
const isLoading = ref(false);
const visible = ref(true);

const handleClose = () => {
    visible.value = false;
};

const sendEmail = (e) => {
    visible.value = true;
    if (!name.value || name.value.length <= 2) {
        return errorMsg.value = "You must enter your full name";
    } else if (!email.value) {
        return errorMsg.value = "You must enter your email address"
    } else if (!message.value) {
        return errorMsg.value = "You must enter your message"
    }

    isLoading.value = true;

    emailjs
        .sendForm(VITE_EMAIL_SERVICE_ID,
            VITE_EMAIL_TEMPLATE_ID,
            emailForm.value,
            VITE_EMAIL_KEY
        )
        .then(
            () => {
                successMsg.value = "Email has been submitted!"
            },
            (error) => {
                errorMsg.value = "Email was not sent. Please contact Annie on LinkedIn!"
            },
        )

    name.value = '';
    email.value = '';
    message.value = '';
    errorMsg.value = '';
    isLoading.value = false;
}
</script>

<template>
    <Container>
        <div class="contact-container">
            <a-divider class="component-header">Contact</a-divider>
            <div class="contact-message">
                <p>
                    If you would like to connect with me for collaboration,
                    a new opportunity, or to socialize, please feel free to reach out to me! ☕️
                </p>
            </div>
            <div class="form-container">
                <form v-if="!isLoading" ref="emailForm" class="contact-form" @submit.prevent="sendEmail">
                    <div class="formfield">
                        <label for="name">Name</label>
                        <a-input v-model:value="name" placeholder=" Your Name" id="name" name="name" />
                    </div>
                    <div class="formfield">
                        <label for="email">Email</label>
                        <a-input type="email" v-model:value="email" placeholder="Your Email" id="email" name="email" />
                    </div>
                    <div class="formfield">
                        <label for="message">Message</label>
                        <a-textarea v-model:value="message" id="message" cols="30" rows="5" placeholder="Your Message"
                            name="message">
                        </a-textarea>
                    </div>
                    <a-button
                        :disabled="isLoading"
                        class="formfield"
                        type="primary"
                        html-type="submit"
                    >
                    Submit
                    </a-button>
                </form>
                <div v-else class="spinner">
                    <a-spin />
                </div>
                <div v-if="errorMsg && !isLoading && visible" class="formfield">
                    <a-alert :message="errorMsg" type="error" :after-close="handleClose" closable />
                </div>
                <div v-else-if="successMsg && !isLoading && visible" class="formfield">
                    <a-alert :message="successMsg" type="success" :after-close="handleClose" closable />
                </div>
            </div>
        </div>
    </Container>
</template>

<style scoped>
.contact-container {
    padding: 40px 0px;
}

.contact-message {
    text-align: center;
}

.form-container {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
}

.formfield {
    width: 50vw !important;
    margin: 10px 0px !important;
}

label {
    font-size: 16px;
    color: var(--dark-blue);
}

.spinner {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 300px;
}

@media screen and (max-width: 600px) {
    .formfield {
        width: 80vw !important;
    }
}
</style>