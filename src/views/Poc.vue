<template>
      <transition name="grid-fade" >
    <div v-if="!buttonState" class="mdc-layout-grid__inner">
            <div class="mdc-layout-grid__cell">
                <div
                class="mdc-card element"
                v-for="(item, index) in firstColumn"
                :key="index"
                @click="showName(item)">
                <div class="card-elements">
                  <em class="material-icons face-icon">{{iconsFirstColumn[index]}}</em>
                  <p class="mdc-card-item"> {{ item }}</p>
                </div>
            </div>
          </div>
            <div class="mdc-layout-grid__cell second-column">
                <div
                class="mdc-card element"
                v-for="(item, index) in secondColumn"
                :key="index"
                @click="showName(item)">
                <div class="card-elements">
                  <em class="material-icons face-icon">{{iconsSecondColumn[index]}}</em>
                  <p class="mdc-card-item">{{ item }}</p>
                </div>
            </div>
          </div>
    </div>
      </transition>
      <div class="buttons-div">
    <div v-if="buttonState" class="mdc-touch-target-wrapper">
        <button
          class="mdc-fab mdc-fab--mini mdc-fab--touch"
          @click="changeButtonState">
          <div class="mdc-fab__ripple"></div>
          <span class="material-icons mdc-fab__icon">add</span>
          <div class="mdc-fab__touch"></div>
        </button>
      </div>
      <!--button active fab code-->
      <div v-else class="mdc-touch-target-wrapper button">
        <button
          class="mdc-fab mdc-fab--mini mdc-fab--touch"
          @click="changeButtonState">
          <div class="mdc-fab__ripple activeBbackround"></div>
          <span class="material-icons mdc-fab__icon activeButton">close</span>
          <div class="mdc-fab__touch"></div>
        </button>
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
    ]);

    const secondColumn = ref([
      "Discharge",
      "Check out",
      "New treatment plan",
      "New calendar event",
      "New group note"
    ]);

    const showName = (itemName) => {
      console.log(itemName);
    };

    const iconsFirstColumn = ref([
      'person_add_alt_1',
      'location_on',
      'medical_services',
      'error',
      'note_add'
      ]);

    const iconsSecondColumn = ref([
      'person_remove',
      'location_off',
      'local_hospital',
      'calendar_today',
      'group_add'


      ]);

    const buttonState = ref(false);

    const changeButtonState = () => {
      buttonState.value = !buttonState.value;
    };

    return {
      firstColumn,
      secondColumn,
      showName,
      buttonState,
      changeButtonState,
      iconsFirstColumn,
      iconsSecondColumn
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
  cursor: pointer;
}
.my-card {
  height: 350px;
  width: 350px;
}
.container {
  width: 45%;
}

.mdc-card-item {
  margin: 0;
}

.face-icon {
 margin-right: 10px;
}

.card-elements {
  display: flex;
  margin-top: 1.2rem;
  margin-left: 1.5rem;
  align-items: center;
}

.face-icon:hover, .card-elements:hover {
  color: #F07E69
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

.mdc-touch-target-wrapper{
  display: inline;
  margin-left: 23rem;
}

.mdc-layout-grid {
padding: 15px;
}

.grid-fade-enter-active, .grid-fade-leave-active {
transition: opacity .5s;
}

.grid-fade-enter-from, .grid-fade-leave-active  {
  opacity: 0;
}

.buttons-div {
position: fixed;
padding: 2em;
left: 50%;
top: 75%;
transform: translateX(-50%);
}

</style>
