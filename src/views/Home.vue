<template>
  <div>
    <h1 class="title">Главная страница планировщика</h1>
    <hr/>
    <p class="subtitle">
      Перейдите на страницу с вашими планами, кликнув соответствующую кнопку снизу.  
    </p>
    <router-link class="link" to="/todos">Перейти в задачи</router-link>
  </div>
</template>

<style lang="scss" scoped>
  p {
    margin-bottom: 2rem;
  }
  .link {
    text-decoration: none!important;
    border: 1px solid#b3d7fd;
    border-radius: 5px;
    padding: 10px 20px;
    color: #499bf3 !important;
    font-weight: 600;

    &:hover {
      opacity: 0.9;
      transition: all 200ms ease 100ms;
      box-shadow: 0 0 10px rgba(0,184,76,0.5)
    }
  }
</style>