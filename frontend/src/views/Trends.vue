<template>
  <div class="trends">
    <!-- Qiita icon -->
    <figure class="card image logo-image">
      <img src="@/assets/qiita.png" />
    </figure>
    <!-- Search Form -->
    <div class="search-form">
      <div class="field">
        <TheInput v-model="state.keywords" label="Keywords"></TheInput>
      </div>
      <div class="field search-button">
        <TheButton value="Search" @button-click="handleClick"></TheButton>
      </div>
    </div>
    <!-- Search List -->
    <div class="search-list">
      <TheTable :tableItems="state.items"></TheTable>
    </div>
  </div>
</template>

<script lang="ts">
/* eslint-disable @typescript-eslint/camelcase */
import axios from 'axios';
import { defineComponent, onMounted, reactive, watch } from 'vue';
import TheButton from '@/components/TheButton.vue';
import TheInput from '@/components/TheInput.vue';
import TheTable from '@/components/TheTable.vue';

export default defineComponent({
  name: 'About',

  components: {
    TheButton,
    TheInput,
    TheTable
  },

  setup() {
    // types
    interface QiitaItem {
      body: string;
      coediting: boolean;
      comments_count: number;
      created_at: string;
      group: null;
      id: string;
      likes_count: number;
      page_views_count: null;
      private: boolean;
      reactions_count: number;
      rendered_body: string;
      tags: string[];
      title: string;
      updated_at: string;
      url: string;
      user: string;
    }

    interface GetQiitaItemParams {
      params: {
        page: number;
        per_page: number;
        query: string;
      };
    }

    type GetQiitaItem = () => void;

    interface TableItems {
      id: string;
      title: string;
      url: string;
    }

    // reactive data
    const state = reactive<{ keywords: string; items: TableItems[] }>({
      keywords: '',
      items: [
        {
          id: '',
          title: '',
          url: ''
        }
      ]
    });

    // button clicked event
    const handleClick: GetQiitaItem = () => {
      axios
        .get('https://qiita.com/api/v2/items', {
          params: {
            page: 1,
            per_page: 20,
            query: state.keywords
          }
        })
        .then(response => {
          const res: QiitaItem[] = response.data;
          const data: TableItems[] = res.map(d => {
            return {
              id: d.id,
              title: d.title,
              url: d.url
            };
          });
          state.items = data;
        });
    };

    return { state, handleClick };
  }
});
</script>

<style lang="scss" scoped>
.card {
  overflow: hidden;
  border-radius: 8px;
  border-left: solid 1px #ddd;
  border-right: solid 1px #ddd;
  border-bottom: solid 5px #888;
}

.logo-image {
  margin: 2vh auto;
  max-width: 20%;
}

.search-form {
  margin: 2vh auto;
  width: 40%;
}

.search-button {
  text-align: right;
}
</style>
