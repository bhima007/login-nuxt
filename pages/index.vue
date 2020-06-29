<template>
  <div class="d-flex justify-center align-center login">
    <div class="d-flex flex-column justify-center align-center login__box">
      <p class="login__title">Log in</p>
      <div class="login__box__input">
        <v-text-field
          v-model="payload.username"
          solo
          flat
          rounded
          light
          color="green"
          background-color="grey lighten-3"
          validate-on-blur
          placeholder="Username"
        ></v-text-field>
        <v-text-field
          v-model="payload.password"
          :append-icon="show ? 'mdi-eye-off' : 'mdi-eye'"
          solo
          flat
          rounded
          :type="show ? 'text' : 'password'"
          light
          color="green"
          background-color="grey lighten-3"
          validate-on-blur
          placeholder="Password"
          @click:append="show = !show"
        ></v-text-field>
      </div>
      <v-btn
        width="300"
        rounded
        depressed
        large
        class="mt-4"
        color="green"
        >Submit</v-btn
      >
      <div class="d-flex flex-column align-center login__social mt-6">
        <p>Or Log in with</p>
        <div>
          <v-btn
            v-for="(item, i) in itemsLogin"
            :key="i"
            fab
            icon
            small
            class="mx-2"
            :class="item"
          >
            <v-icon>mdi-{{ item }}</v-icon>
          </v-btn>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      itemsLogin: ['gmail', 'facebook', 'twitter'],
      payload: {
        username: '',
        password: '',
      },
      rules: {
        required: (value) => !!value || 'Required.',
        min: (v) => v.length >= 6 || 'Min 6 characters',
        emailMatch: () => "The email and password you entered don't match",
      },
    }
  },
}
</script>

<style lang="sass" scoped>
.login
  margin: 0
  position: absolute
  top: 50%
  left: 50%
  margin-right: -50%
  transform: translate(-50%, -50%)
  &__title
    font-size: 32px
    font-weight: 500
  &__box
    width: 450px
    border-radius: 12px
    &__input
      width: 300px
  &__social
    font-size: 12px
    font-weight: 500
</style>
