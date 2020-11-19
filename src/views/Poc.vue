<template>
  <div class="mdc-layout-grid">
    <div class="mdc-layout-grid__inner">
      <!--first column-->
      <transition name="fade">

            <div v-show="!buttonState" class="mdc-layout-grid__cell">
                <div
                class="mdc-card element"
                v-for="(item, index) in firstColumn"
                :key="index"
                @click="showName(item)"
                >
                <p>
                    <i class="material-icons">face</i>
                    {{ item }}
                </p>
                </div>
            </div>
      
      </transition>
      <!--button inactive fab code-->
      <div v-if="buttonState" class="mdc-touch-target-wrapper">
        <button
          class="mdc-fab mdc-fab--mini mdc-fab--touch"
          @click="changeButtonState"
        >
          <div class="mdc-fab__ripple"></div>
          <span class="material-icons mdc-fab__icon">add</span>
          <div class="mdc-fab__touch"></div>
        </button>
      </div>
      <!--button active fab code-->
      <div v-else class="mdc-touch-target-wrapper button">
        <button
          class="mdc-fab mdc-fab--mini mdc-fab--touch"
          @click="changeButtonState"
        >
          <div class="mdc-fab__ripple activeBbackround"></div>
          <span class="material-icons mdc-fab__icon activeButton">close</span>
          <div class="mdc-fab__touch"></div>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "Poc",
  setup() {
    const firstColumn = ref([
      "New initake",
      "Check in",
      "New medication",
      "New incident",
      "New progress note",
      "Discharge",
      "Check out",
      "New treatment plan",
      "New calendar event",
      "New group note"
    ]);

    const showName = (itemName) => {
      console.log(itemName);
    };

    const buttonState = ref(false);

    const changeButtonState = () => {
      buttonState.value = !buttonState.value;
      /***
    Aqui tienes que investigar como mandar a llamar la animación
    de Keyframes o la que quieras, si es keyframes mandas a llamar
    el evento aquí dentro, si es CCS puro, añade el la propiedad de CSS
    a los divs, y ponle una propiedad reactiva para que se apague y prenda
    el hover por ejemplo, o lo que sea la animación
    ***/
    };

    return {
      firstColumn,
      showName,
      buttonState,
      changeButtonState,
    };
  },
};
</script>

<style scoped>
.my-card-content {
  padding: 16px;
  width: 30%;
}
.mdc-card {
  box-shadow: 0px 1px 9px 0px rgba(50, 50, 50, 0.77);
  height: 60px;
  border-radius: 8px;
}
.mdc-card:hover {
  box-shadow: -3px 19px 17px 0px rgba(57, 50, 50, 0.65);
}
.my-card {
  height: 350px;
  width: 350px;
}
.container {
  width: 45%;
}

/**button inactive fab code*/

.mdc-fab__ripple {
  background-color: rgb(52, 203, 203);
}
.mdc-fab__icon {
  color: black;
}
.element {
  margin-bottom: 15px;
}
/**button active fab code*/
.activeButton {
  color: rgb(52, 203, 203);
}
.activeBbackround {
  background-color: rgb(0, 51, 102);
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

</style>
