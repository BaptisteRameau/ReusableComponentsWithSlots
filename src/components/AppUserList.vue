<template>
  <section>
    <slot name="title">Users</slot>
    <slot
      name="userlist"
      :count="data.results.length"
      :list="data.results"
      :remove="remove"
      v-if="state === states.loaded"
    >
      <ul class="userlist">
        <li v-for="item in data.results" :key="item.email">
          <slot name="listitem" :user="item">
            <div>
              <img
                width="48"
                height="48"
                :src="item.picture.large"
                :alt="item.name.first + ' ' + item.name.last"
              />
              <div>
                <div>{{ item.name.first }}</div>
                <slot name="secondrow" :item="item" :remove="remove"></slot>
              </div>
            </div>
          </slot>
        </li>
      </ul>
    </slot>
    <slot v-else-if="state === states.loading" name="loading">
      loading...
    </slot>
    <slot v-else name="error">
      Oops, something went wrong.
    </slot>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const states = {
  idle: "idle",
  loading: "loading",
  loaded: "loaded",
  failed: "failed"
}

const state = ref(states.idle);
const data = ref(undefined);

const load = async () => {
  state.value = states.loading;
  try {
    const response = await fetch("https://randomuser.me/api/?results=5");
    const json = await response.json();
    data.value = json;
    state.value = states.loaded;
  } catch (error) {
    state.value = states.failed;
    console.error(error);
  }
};

onMounted(() => {
  load();
});

const remove = (item) => {
  data.value.results = data.value.results.filter(
    (entry) => entry.email !== item.email
  );
};
</script>

<style scoped>
.userlist {
  margin: 10px;
}
.userlist img {
  border-radius: 50%;
  margin-right: 1rem;
}

.userlist li + li {
  margin-top: 10px;
}

.userlist li > div {
  display: flex;
  align-items: center;
}

.userlist li div div {
  flex: 1;
}
</style>
