<template>
  <b-container>
    <b-row>
      <b-col>
        <b-form-textarea
          id="textarea"
          v-model="text"
          placeholder="Enter something..."
          rows="3"
          max-rows="6"
        ></b-form-textarea>
      </b-col>
      <b-col>
        <b-form-textarea
          id="textarea"
          v-model="text"
          placeholder="Enter something..."
          rows="3"
          max-rows="6"
        ></b-form-textarea>
      </b-col>
    </b-row>
  </b-container>
</template>
<style lang="scss" scoped>
textarea {
  width: 100%;
}
</style>
