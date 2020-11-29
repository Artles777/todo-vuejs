<template>
  <div>
    <p class="todo-non">
      Добавьте новую задачу для вашего планировщика.
    </p>
    <button class="add" @click="modal = true">+</button>
    <div class="modal" :class="{active: modal === true}">
        <div class="modal-mask">
          <div class="modal-wrapper">
            <div class="modal-container">
              <button class="modal-close" @click="modal = false">&times;</button>

              <div class="modal-header">
                <slot name="header">
                  <h3 class="modal-title">
                    Добавьте новую задачу
                  </h3>
                </slot>
              </div>

              <div class="modal-content">
                <slot name="content">
                  <span class="modal-subtitle">Название новой задачи:</span>
                  <AddTodo @add-todo="$emit('add-todo', $event)" />
                </slot>
              </div>

            </div>
          </div>
        </div>
    </div>
  </div>
</template>

<script>
import AddTodo from '@/components/AddTodo'
export default {
  data () {
    return {
      modal: false
    }
  },
  components: {
    AddTodo
  }
}
</script>

<style lang="scss" scoped>
  .add {
    font-size: 2rem;
    border: 1px solid #ccc;
    background: linear-gradient(-45deg, #00b84c 49%, #0D61BC 45%, #8ad6cc);
    background-clip: text;
    -webkit-text-fill-color: transparent;
    color: transparent;
    font-weight: 700;
    border-radius: 3rem;
    height: 3rem;
    width: 3rem;
    outline: none;
  }
  .add:hover {
    border-color: #00b84c;
    cursor: pointer;
  }
  .modal {
    display: none;

    &-mask {
      display: flex;
      justify-content: center;
      position: fixed;
      z-index: 1000;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
    }

    &-wrapper {
      display: flex;
      align-items: center;
    }

    &-container {
      width: 500px;
      margin: 0px auto;
      padding: 20px 30px;
      background-color: #fff;
      position: relative;
    }

    &-subtitle {
      margin-bottom: 1rem;
    }

    &-close {
      position: absolute;
      top: 0;
      right: 0;
      margin-right: 10px;
      margin-top: 10px;
    }
  }
  .active {
    display: block;
  }
</style>

<style lang="scss">
  .modal {
    &-content {
      .todo-add {
        margin-top: 1rem;

        &-wrapper {
          width: 100%;
        }

        &-field {
          width: 100%;
        }
      }
    }
  }
</style>

