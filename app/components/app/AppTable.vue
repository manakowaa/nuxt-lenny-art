<template>
  <table class="app-table">
    <thead class="app-table__thead">
      <tr class="app-table__head-tr">
        <th class="app-table__th"></th>
        <th
          v-for="(th, thIndex) in headers"
          :key="thIndex"
          class="app-table__th">
          {{ th }}
    </th>
      </tr>
    </thead>
    <tbody class="app-table__body">
      <tr v-for="(tr, trIndex) in rows" :key="trIndex" class="app-table__tr">
        <th class="app-table__body-th">
             {{ tr.header }}
        </th>
        <td v-for="(td, tdIndex) in tr.values" :key="tdIndex" class="app-table__td">
            <span v-if="td && typeof td === 'boolean'" class="app-table__ok"></span>
        
        <template v-else>
            {{ td }}
        </template>
        </td>

      </tr>

    </tbody>
    <tfoot class="app-table__footer">
      <tr class="app-table__footer-tr">
        <th class="app-table__footer-th"></th>
        <th
          v-for="(th, thIndex) in headers"
          :key="thIndex"
          class="app-table__footer-th"
        >
          {{ th }}
        </th>
      </tr>
    </tfoot>
  </table>
</template>

<script setup>
const props = defineProps({
  data: {
    type: Object,
    default: () => ({}),
  },
});

const headers = computed(() =>
  Array.isArray(props.data.headers) ? props.data.headers : [],
);

const rows = computed(() =>
  Array.isArray(props.data.data) ? props.data.data : [],
);
</script>

<style lang="less">
.app-table {
  width: 100%;
  border-collapse: collapse;
  color: @black;
  text-align: center;
  @media @bw768 {
    margin: 0 -20px;
    width: calc(100% + 40px);
  }

  &__head,
  &__body,
  &__footer {
    @media @bw768 {
      display: block;
    }
  }
  &__head-tr {
    @media @bw768 {
      display: flex;
      width: 100%;
    }
  }

  &__tr {
    @media @bw768 {
      display: flex;
      flex-wrap: wrap;
    }
    &:nth-child(2n-1) {
      background-color: fade(@black, 3%);
      @media @bw768 {
        background-color: transparent;
      }
    }
  }

  &__th {
    height: 85px;
    text-transform: uppercase;
    font-weight: 600;
    font-size: 18px;
    line-height: 25px;
    @media @bw768 {
      font-size: 14px;
      line-height: 19px;
    }
  }

  &__footer-th {
    height: 60px;
    font-size: 0;
    @media @bw768 {
      font-size: 16px;
      font-weight: 300;
    }
  }

  &__th,
  &__footer-th {
    box-sizing: border-box;
    padding: 10px;
    border-right: 1px solid @gray_dark;
    text-transform: uppercase;
    @media @bw768 {
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      width: 33.3333%;
    }

    &:first-child {
      padding-left: 0;
      @media @bw768 {
        display: none;
      }
    }
    &:last-child {
      border-right: none;
      padding-right: 0;
    }
  }

  &__body-th {
    box-sizing: border-box;
    height: 50px;
    padding: 10px 10px 10px 0;
    border-top: 1px solid @gray_dark;
    border-bottom: 1px solid @gray_dark;
    font-weight: 400;
    font-size: 18px;
    line-height: 25px;
    text-align: left;
    @media @bw768 {
      display: block;
      width: 100%;
      text-align: center;
      font-weight: 600;
    }
  }

  &__td {
    box-sizing: border-box;
    height: 50px;
    padding: 10px;
    border: 1px solid @gray_dark;
    font-weight: 600;
    font-size: 16px;
    line-height: 22px;
    @media @bw768 {
      width: 33.3333%;
    }
    &:last-child {
      border-right: none;
      padding-right: 0;
    }
    &:nth-child(2n-1) {
      @media @bw768 {
        background-color: fade(@black, 3%);
      }
    }
  }

  &__footer-tr {
    @media @bw768 {
      display: flex;
    }
  }

  &__ok {
    display: block;
    position: relative;
    margin: auto;
    width: 26px;
    height: 26px;
    border-radius: 50%;
    background-color: @black;
    &::after {
      content: "";
      position: absolute;
      left: 9px;
      top: 4px;
      width: 6px;
      height: 12px;
      border-right: 2px solid @white;
      border-bottom: 2px solid @white;
      transform: rotate(45deg);
    }
  }
}
</style>
