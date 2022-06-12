<template>
  <div class="home">
    <div class="flex w-full justify-end">
      <button
        type="button"
        @click="toggleHidden()"
        class="
          mb-12
          px-5
          py-3
          text-base
          font-medium
          text-center text-white
          bg-blue-700
          rounded-lg
          hover:bg-blue-800
          focus:ring-4 focus:outline-none focus:ring-blue-300
          dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800
        "
      >
        Create product
      </button>
    </div>
    <div
      v-if="!isHidden"
      class="
        absolute
        z-50
        w-screen
        h-screen
        bg-black bg-opacity-30
        flex
        justify-center
        items-center
        top-0
        left-0
      "
    >
      <form
        class="
          flex
          m-auto
          bg-white
          rounded-md
          drop-shadow-xl
          p-12
          gap-12
          flex-wrap
          w-1/2
        "
        enctype="multipart/form-data"
      >
        <div class="left flex-1 flex flex-col gap-8">
          <div>
            <label
              for="first_name"
              class="
                block
                mb-2
                text-base
                font-medium
                text-gray-900
                dark:text-gray-300
              "
              >Product name</label
            >
            <input
              type="text"
              class="
                bg-gray-50
                border border-gray-300
                text-gray-900 text-sm
                rounded-lg
                focus:ring-blue-500 focus:border-blue-500
                block
                w-full
                p-2.5
                dark:bg-gray-700
                dark:border-gray-600
                dark:placeholder-gray-400
                dark:text-white
                dark:focus:ring-blue-500
                dark:focus:border-blue-500
              "
              placeholder="Product"
              required
              v-model="productName"
            />
          </div>
          <div>
            <label
              for="first_name"
              class="
                block
                mb-2
                text-base
                font-medium
                text-gray-900
                dark:text-gray-300
              "
              >Product price</label
            >
            <input
              type="number"
              step="0.01"
              class="
                bg-gray-50
                border border-gray-300
                text-gray-900 text-sm
                rounded-lg
                focus:ring-blue-500 focus:border-blue-500
                block
                w-full
                p-2.5
                dark:bg-gray-700
                dark:border-gray-600
                dark:placeholder-gray-400
                dark:text-white
                dark:focus:ring-blue-500
                dark:focus:border-blue-500
              "
              placeholder="150.50"
              required
              v-model="productPrice"
            />
          </div>
          <div>
            <label
              class="
                block
                mb-2
                text-base
                font-medium
                text-gray-900
                dark:text-gray-300
              "
              for="default_size"
              >Product image</label
            >
            <input @change="getImages" type="file" id="image" name="image" />
          </div>
        </div>
        <div class="right flex-1 flex flex-col gap-8">
          <div>
            <label
              for="message"
              class="
                block
                mb-2
                text-sm
                font-medium
                text-gray-900
                dark:text-gray-400
              "
              >Product description</label
            >
            <textarea
              id="message"
              rows="8"
              class="
                block
                p-2.5
                w-full
                text-sm text-gray-900
                bg-gray-50
                rounded-lg
                border border-gray-300
                focus:ring-blue-500 focus:border-blue-500
                dark:bg-gray-700
                dark:border-gray-600
                dark:placeholder-gray-400
                dark:text-white
                dark:focus:ring-blue-500
                dark:focus:border-blue-500
              "
              placeholder="Your description..."
              required
              v-model="productDescription"
            ></textarea>
          </div>
          <button
            @click.prevent="addProduct"
            type="button"
            class="
              px-5
              py-3
              text-base
              font-medium
              text-center text-white
              bg-blue-700
              rounded-lg
              hover:bg-blue-800
              focus:ring-4 focus:outline-none focus:ring-blue-300
              dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800
            "
          >
            Create
          </button>
        </div>
      </form>
    </div>
    <div class="productDiv mt-4">
      <div class="filterDiv flex mt-12 mb-4 w-full gap-12 flex-wrap">
        <div class="filter flex-1">
          <label
            for="default"
            class="
              block
              mb-2
              text-lg
              font-medium
              text-gray-900
              dark:text-gray-400
            "
            >Category:
          </label>
          <select
            id="default"
            class="
              bg-gray-50
              border border-gray-300
              text-gray-900
              mb-6
              text-base
              rounded-lg
              focus:ring-blue-500 focus:border-blue-500
              block
              w-full
              p-2.5
              dark:bg-gray-700
              dark:border-gray-600
              dark:placeholder-gray-400
              dark:text-white
              dark:focus:ring-blue-500
              dark:focus:border-blue-500
            "
          >
            <option selected>Choose a category</option>
            <option value="US">United States</option>
            <option value="CA">Canada</option>
            <option value="FR">France</option>
            <option value="DE">Germany</option>
          </select>
        </div>
        <div class="sort flex-1">
          <label
            for="default"
            class="
              block
              mb-2
              text-lg
              font-medium
              text-gray-900
              dark:text-gray-400
            "
            >Sort:
          </label>
          <div class="flex">
            <div class="flex items-center mr-4">
              <input
                id="inline-radio"
                type="radio"
                value=""
                name="inline-radio-group"
                class="
                  w-4
                  h-4
                  text-blue-600
                  bg-gray-100
                  border-gray-300
                  focus:ring-blue-500
                  dark:focus:ring-blue-600 dark:ring-offset-gray-800
                  focus:ring-2
                  dark:bg-gray-700 dark:border-gray-600
                "
              />
              <label
                for="inline-radio"
                class="
                  ml-2
                  text-base
                  font-medium
                  text-gray-900
                  dark:text-gray-300
                "
                >By Name</label
              >
            </div>
            <div class="flex items-center mr-4">
              <input
                id="inline-2-radio"
                type="radio"
                value=""
                name="inline-radio-group"
                class="
                  w-4
                  h-4
                  text-blue-600
                  bg-gray-100
                  border-gray-300
                  focus:ring-blue-500
                  dark:focus:ring-blue-600 dark:ring-offset-gray-800
                  focus:ring-2
                  dark:bg-gray-700 dark:border-gray-600
                "
              />
              <label
                for="inline-2-radio"
                class="
                  ml-2
                  text-base
                  font-medium
                  text-gray-900
                  dark:text-gray-300
                "
                >By Price</label
              >
            </div>
          </div>
        </div>
      </div>
      <div class="productsDiv">
        <h1 class="text-2xl font-bold mb-8">Products List</h1>
        <div class="grid grid-cols-1 gap-12 md:grid-cols-2 xl:grid-cols-4">
          <Product
            v-for="product in products"
            :name="product.name"
            :description="product.description"
            :price="product.price"
            :image="product.image"
            :key="product.id"
          />
        </div>
      </div>
    </div>
  </div>
  <nav aria-label="Page navigation example">
    <ul class="inline-flex items-center -space-x-px mt-8">
      <li @click="goToPage(currentPage - 1)">
        <span
          class="
            block
            py-2
            px-3
            ml-0
            leading-tight
            text-gray-500
            bg-white
            rounded-l-lg
            border border-gray-300
            hover:bg-gray-100 hover:text-gray-700
            dark:bg-gray-800
            dark:border-gray-700
            dark:text-gray-400
            dark:hover:bg-gray-700
            dark:hover:text-white
          "
        >
          <span class="sr-only">Previous</span>
          <svg
            class="w-5 h-5"
            fill="currentColor"
            viewBox="0 0 20 20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              d="M12.707 5.293a1 1 0 010 1.414L9.414 10l3.293 3.293a1 1 0 01-1.414 1.414l-4-4a1 1 0 010-1.414l4-4a1 1 0 011.414 0z"
              clip-rule="evenodd"
            ></path>
          </svg>
        </span>
      </li>
      <li
        v-for="number in pagesCount"
        :key="number"
        :style="
          number + 1 !== currentPage ? 'cursor: pointer' : 'cursor: not-allowed'
        "
        @click="goToPage(number + 1)"
      >
        <span
          class="
            py-2
            px-3
            leading-tight
            text-gray-500
            bg-white
            border border-gray-300
            hover:bg-gray-100 hover:text-gray-700
            dark:bg-gray-800
            dark:border-gray-700
            dark:text-gray-400
            dark:hover:bg-gray-700
            dark:hover:text-white
          "
        >
          {{ number + 1 }}
        </span>
      </li>
      <li
        :style="
          currentPage === pagesCount ? 'cursor: pointer' : 'cursor: not-allowed'
        "
        @click="goToPage(currentPage + 1)"
      >
        <span
          class="
            block
            py-2
            px-3
            leading-tight
            text-gray-500
            bg-white
            rounded-r-lg
            border border-gray-300
            hover:bg-gray-100 hover:text-gray-700
            dark:bg-gray-800
            dark:border-gray-700
            dark:text-gray-400
            dark:hover:bg-gray-700
            dark:hover:text-white
          "
        >
          <span class="sr-only">Next</span>
          <svg
            class="w-5 h-5"
            fill="currentColor"
            viewBox="0 0 20 20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z"
              clip-rule="evenodd"
            ></path>
          </svg>
        </span>
      </li>
    </ul>
  </nav>
</template>
<script setup>
import { ref, onMounted } from "vue";
import Product from "../components/productCard.vue";

const isHidden = ref(true);
const products = ref([]);
const pagesCount = ref([]);
const currentPage = ref(1);

// create a new product
const productName = ref("");
const productDescription = ref("");
const productPrice = ref("");
const productCategory = ref(1);
const productImage = ref(null);

const addProduct = async () => {
  var formdata = new FormData();
  formdata.append("name", productName.value);
  formdata.append("price", productPrice.value);
  formdata.append("description", productDescription.value);
  formdata.append("image", productImage.value);
  console.log(productImage.value);
  var requestOptions = {
    method: "POST",
    body: formdata,
    redirect: "follow",
  };

  fetch("http://localhost:8000/api/v1/products", requestOptions)
    .then((response) => response.json())
    .then((result) => console.log(result))
    .catch((error) => console.log("error", error));
};

const getImages = (event) => {
  productImage.value = event.target.files[0];
};

const toggleHidden = () => {
  isHidden.value = !isHidden.value;
};

const goToPage = async (page) => {
  const response = await fetch(
    `http://localhost:8000/api/v1/products?page=${page}`
  );
  const result = await response.json();
  currentPage.value = result.current_page;
  products.value = result.data;
  pagesCount.value = Array.from(
    Array(Math.ceil(result.total / result.per_page)).keys()
  );
};

onMounted(async () => {
  const resposnse = await fetch("http://localhost:8000/api/v1/products");
  const result = await resposnse.json();
  currentPage.value = result.current_page;
  products.value = result.data;
  pagesCount.value = Array.from(
    Array(Math.ceil(result.total / result.per_page)).keys()
  );
});
</script>

<style lang="scss" scoped>
.home {
  .formDiv {
    margin: auto;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
    padding: 50px;
    display: flex;
    gap: 50px;
    justify-content: center;
    flex-wrap: wrap;
    .left {
      display: flex;
      flex-direction: column;
      flex: 1;
      gap: 30px;
    }
    .right {
      display: flex;
      flex-direction: column;
      flex: 1;
      gap: 30px;
    }
    .inputElement {
      border: 1px solid #d9d9d9;
      border-radius: 10px;
      min-width: 90%;
      padding: 15px 20px;
      color: #162642;
      font-size: 18px;
      &::placeholder {
        color: #5a5a5a;
        font-size: 14px;
      }
      &:focus {
        outline: none !important;
      }
    }
  }
}
</style>
