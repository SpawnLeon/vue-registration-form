<template>

  <button class="btn"
          :class="classes"
          :disabled="disabled">
    <slot />
  </button>

</template>

<script>
export default {
  name: 'AppButton',
  props: {
    disabled: Boolean,
    classes: String,
  },

};
</script>

<style scoped
       lang="scss">
.btn {
  background-color : #0880ae;
  box-shadow       : 0 2px 4px rgba(44, 39, 56, 0.08), 0px 4px 8px rgba(44, 39, 56, 0.08);
  border-radius    : 6px;
  padding          : 17px 17px 16px 17px;
  width            : 100%;
  border           : 2px solid transparent;
  cursor           : pointer;
  font-weight      : 500;
  font-size        : 16px;
  line-height      : 1.2125;
  text-align       : center;

  color            : #ebf4f8;

  &:hover {
    box-shadow : 0 12px 24px rgba(44, 39, 56, 0.08), 0 24px 48px rgba(44, 39, 56, 0.16);
  }

  &:focus {
    border-color : rgba(44, 39, 56, 0.86);
  }

  &:disabled {
    background-color : #dbe2ea;
    box-shadow       : 0 2px 4px rgba(44, 39, 56, 0.08), 0 4px 8px rgba(44, 39, 56, 0.08);
    color            : #b1b5bf;
    cursor           : not-allowed;
  }
}
</style>
