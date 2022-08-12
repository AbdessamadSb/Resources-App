<template>
  <li class="m-auto max-w-[40rem]">
    <base-card>
      <div>
        <header class="flex justify-between items-center">
          <h3 class="my-2 text-xl">{{ title }}</h3>
          <base-button mode="flat" @click="deleteRes(id)">Delete</base-button>
        </header>
      </div>
      <p class="my-2">{{ description }}</p>
      <nav>
        <a
          class="no-underline text-[#ce5c00] active:text-[#c89300] hover:text-[#c89300]"
          :href="link"
          >View Resource</a
        >
      </nav>
    </base-card>
  </li>
</template>

<script>
export default {
  props: ["id", "title", "description", "link"],
  inject: ["deleteRes"],
};
</script>
