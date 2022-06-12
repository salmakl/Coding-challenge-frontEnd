
<template>
  <div>
    <a
      href="#"
      class="group h-96 block bg-gray-100 rounded-t-lg overflow-hidden relative"
    >
      <img
        :src="`http://localhost:8000/images/${image}`"
        loading="lazy"
        alt="Photo by Austin Wade"
        class="
          w-full
          h-full
          object-cover object-center
          group-hover:scale-110
          transition
          duration-200
        "
      />
      >
    </a>

    <div
      class="
        flex
        justify-between
        items-start
        bg-gray-100
        rounded-b-lg
        gap-2
        p-4
      "
    >
      <div class="flex flex-col">
        <a
          href="#"
          class="
            text-gray-800
            hover:text-gray-500
            lg:text-lg
            font-bold
            transition
            duration-100
          "
          >{{ name }}</a
        >
        <span class="text-gray-500 text-sm lg:text-base">{{
          description
        }}</span>
      </div>

      <div class="flex flex-col items-end">
        <span class="text-gray-600 lg:text-lg font-bold">{{ price }}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  name: String,
  price: Number,
  image: String,
  description: String,
  categories: Array,
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
