<template>
  <div :class="['task-card', { done: done }]">
    <div>
      <h3>{{ title }}</h3>
      <p>{{ description }}</p>
    </div>
    <div>{{ done ? "✅" : "⭕️" }}</div>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    description: String,
    done: { type: Boolean, default: false}
  },
  data() {
    return {};
  },
};
</script>

<style lang="scss">
.task-card {
  display: flex;
  min-height: 6rem;
  text-align: left;
  background-color: saturate(rgba(#41b883, 0.03), 30%);
  border-bottom: solid 1px rgba(#35495e, 0.1);
  border-left: solid 8px #41b883;
  transition: all 0.3s;
  p { font-size: 0.9rem; }
  &:hover {
    transform: scale(1.02);
    background-color: white;
    box-shadow: 2px 3px 10px rgba(black, 0.1);
  }
  & > div:first-child {
    margin: 0 1rem;
    padding: 1rem 0;
    display: flex;
    flex-grow: 1;
    flex-direction: column;
    justify-content: center;
  }
  &.done {
    border-left: solid 8px rgba(#35495e, 0.3);
    background-color: rgba(#35495e, 0.08);
    h3, p { text-decoration: line-through; opacity: 0.3; }
    &:hover { transform: unset; box-shadow: unset; }
  }
}
</style>
