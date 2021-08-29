<template>
  <div class="container">
    <div class="tile is-ancestor is-vertical">
      <div class="tile is-child box field has-addons">
        <p class="control">
          <span class="select">
            <select>
              <option>Français</option>
            </select>
          </span>
        </p>
        <p class="control is-expanded has-icons-left">
          <input class="input" type="text" placeholder="" autofocus>
          <span class="icon is-small is-left">
            <i class="fas fa-search"></i>
          </span>
        </p>
        <p class="control">
          <a class="button is-static">XX questions</a>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
}
</script>

<style lang="scss">
  @import "./scss/main.scss";
</style>
