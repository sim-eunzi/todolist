<template>
  <div>
    <h1>TODO LIST</h1>
    <ol class="breadcrumb">
      <li class="breadcrumb-item">
        <router-link to="/">All</router-link>
      </li>
      <li class="breadcrumb-item">
        <router-link to="/active">Active</router-link>
      </li>
      <li class="breadcrumb-item">
        <router-link to="/clear">Clear</router-link>
      </li>
    </ol>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';

@Component
export default class Header extends Vue {}
</script>

<style>
</style>