<template>
  <form @submit.prevent="submit">
    <Input
      v-model="email"
      label="Your email:"
      id="emailNewsletter"
      type="email"
      name="email"
    />
    <div>
      <label for="messageNewsletter">Your message:</label>
      <textarea id="messageNewsletter" name="message"></textarea>
    </div>

    <!-- your other form fields go here 
    action="https://formspree.io/f/xqknbvee" method="POST"-->
    <button type="submit">Send</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: "",
    };
  },
  methods: {
    submit() {
      fetch('https://formspree.io/f/xqknbvee', {
        method: 'POST',
        body: JSON.stringify({
          'input' : this.email,
        }),
        headers: {
          'Accept': "application/json",
          'Content-type' : "application/json"
        },
      })
        .then((response) => {
          if (response.ok) {
            console.log("Thanks for your submission!");
            form.reset();
          } else {
            response.json().then((data) => {
              if (Object.hasOwn(data, "errors")) {
                console.log(data["errors"])
                  .map((error) => error["message"])
                  .join(", ");
              } else {
                
                  console.log("Oops! There was a problem submitting your form");
              }
            });
          }
        })
        .catch((error) => {
          console.log("Oops! There was a problem submitting your form");
        });
    },
  },
};
</script>
