<template>
  <div class="page">
    <h4>Thêm liên hệ</h4>

    <ContactForm :contact="contact" @submit:contact="saveContact" />
  </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
  components: {
    ContactForm,
  },

  data() {
    return {
      contact: {
        name: "",
        email: "",
        address: "",
        phone: "",
        favorite: false,
      },
    };
  },

  methods: {
    async saveContact(data) {
      try {
        await ContactService.create(data);

        alert("Thêm liên hệ thành công!");

        this.$router.push({
          name: "contactbook",
        });
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
