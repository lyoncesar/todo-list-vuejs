<template>
  <form class="stack-small" @submit.prevent="onSubmit">
    <div>
      <label class="edit-label">Edit Name for &quot;{{label}}&quot;</label>

      <!-- The .lazy is use the change event instead input event. This means that Vue will only sync data when the input loses focus or the form is submitted. -->
      <input type="text" :id="id" ref="labelInput" autocomplete="off" v-model.lazy.trim="newLabel" />
    </div>
    <div class="btn-group">
      <button type="buttom" class="btn" @click="onCancel">
        Cancel
        <span class="visually-hidden">editing {{label}}</span>
      </button>
      <button type="submit" class="btn btn__primary"> 
        Save
        <span>editing for {{label}}</span>
      </button>
    </div>
  </form>
</template>
<script>
export default {
  props: {
    id: {
      type: String,
      required: true
    },
    label: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      newLabel: this.label
    };
  },
  methods: {
    onSubmit() {
      if (this.newLabel && this.newLabel !== this.label) {
        this.$emit("item-edited", this.newLabel);
      }
    },
    onCancel() {
      this.$emit("edit-canceled");
    }
  },
  mounted() {
    const labelInputRef = this.$refs.labelInput;
    labelInputRef.focus();
  }
};
</script>
<style scoped>
.edit-label {
  font-family: Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #0b0c0c;
  display: block;
  margin-bottom: 5px;
}
input {
  display: inline-block;
  margin-top: 0.4rem;
  width: 100%;
  min-height: 4.4rem;
  padding: 0.4rem 0.8rem;
  border: 2px solid #565656;
}
form {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
form > * {
  flex: 0 0 100%;
}
</style>
