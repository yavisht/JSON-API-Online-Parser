<template>
  <div>
    <b-jumbotron>
      <template v-slot:header
        >JSON:API Live Parser</template
      >

      <template v-slot:lead
        >Paste a JSON:API response, we will parse it for you ;)</template
      >

      <hr class="my-4" />

      <p>
        It uses utility classes for typography and spacing to space content out
        within the larger container.
      </p>

      <b-button
        variant="success"
        href="https://github.com/yavisht/JSON-API-Online-Parser"
        >View on GitHub</b-button
      >
    </b-jumbotron>
    <b-container fluid>
      <b-row>
        <b-col>
          <b-button
            v-if="jsonRaw"
            variant="primary"
            href="#"
            @click.prevent="parseData()"
            >Do Something</b-button
          >
          <b-button
            v-if="jsonParsed"
            variant="danger"
            href="#"
            @click.prevent="reset()"
            >Reset</b-button
          >
        </b-col>
      </b-row>
      <b-row>
        <b-col v-if="!jsonParsed" sm="12">
          <b-form-textarea
            id="textarea"
            v-model="jsonRaw"
            placeholder="Paste some JSON"
            rows="10"
            max-rows="20"
          ></b-form-textarea>
        </b-col>
        <b-col v-if="jsonParsed" sm="12">
          <vue-json-pretty
            :show-select-controller="true"
            :select-on-click-node="true"
            :show-length="true"
            :show-line="true"
            :show-double-quotes="true"
            :highlight-mouseover-node="true"
            :highlight-selected-node="true"
            :deep="2"
            :data="jsonParsed"
          ></vue-json-pretty>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
import jsonapi from 'jsonapi-parse'
import VueJsonPretty from 'vue-json-pretty'

export default {
  components: {
    VueJsonPretty
  },
  data() {
    return {
      jsonRaw: '',
      jsonParsed: ''
    }
  },
  methods: {
    parseData() {
      this.jsonParsed = jsonapi.parse(this.jsonRaw)
      this.jsonRaw = ''
    },
    reset() {
      this.jsonParsed = ''
      this.jsonRaw = ''
    }
  }
}
</script>
<style lang="scss" scoped>
.col {
  .btn {
    margin-bottom: 15px;
  }
}
</style>
