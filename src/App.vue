<template>
  <div class="calc" id="app">
    <h1 class="calc__title">Счётчик калорий</h1>
    <div class="calc__inner">
      <div class="sex">
        <h2 class="sex__title">Пол</h2>
        <div class="sex_item-wrapper">
          <input
            class="sex__radio"
            type="radio"
            name="sex"
            id="male"
            value="male"
            v-model="sex"
          />
          <label class="sex__label" for="male">Мужчина</label>
        </div>
        <div class="sex_item-wrapper">
          <input
            class="sex__radio"
            type="radio"
            name="sex"
            id="female"
            value="female"
            v-model="sex"
          />
          <label class="sex__label" for="female">Женщина</label>
        </div>
      </div>

      <div class="indicators">
        <div class="indicators__item-wrapper">
          <label class="indicators__label" for="age"
            >Возраст <span>лет</span></label
          >
          <input
            class="indicators__input"
            type="text"
            name="age"
            id="age"
            placeholder="0"
            v-model="age"
            v-on:input="changeStateBtn()"
          />
        </div>
        <div class="indicators__item-wrapper">
          <label class="indicators__label" for="grow"
            >Рост <span>см</span></label
          >
          <input
            class="indicators__input"
            type="text"
            name="grow"
            id="grow"
            placeholder="0"
            v-model="height"
            v-on:input="changeStateBtn()"
          />
        </div>
        <div class="indicators__item-wrapper">
          <label class="indicators__label" for="weight"
            >Вес <span>кг</span></label
          >
          <input
            class="indicators__input"
            type="text"
            name="weight"
            id="weight"
            placeholder="0"
            v-model="weight"
            v-on:input="changeStateBtn()"
          />
        </div>
      </div>

      <div class="activity">
        <h2 class="activity__title">Физическая активность</h2>
        <div class="activity__inner">
          <div class="activity__item-wrapper">
            <input
              class="activity__radio"
              type="radio"
              name="activity"
              id="minimal"
              value="1.2"
              v-model="activity"
            />
            <label class="activity__label" for="minimal"
              >Минимальная
              <span>Сидячая работа и нет физических нагрузок</span>
            </label>
          </div>
          <div class="activity__item-wrapper">
            <input
              class="activity__radio"
              type="radio"
              name="activity"
              id="low"
              value="1.375"
              v-model="activity"
            />
            <label class="activity__label" for="low"
              >Низкая
              <span>Редкие, нерегулярные тренировки, активность в быту</span>
            </label>
          </div>
          <div class="activity__item-wrapper">
            <input
              class="activity__radio"
              type="radio"
              name="activity"
              id="middle"
              value="1.55"
              v-model="activity"
            />
            <label class="activity__label" for="middle"
              >Средняя
              <span>Тренировки 3-5 раз в неделю</span>
            </label>
          </div>
          <div class="activity__item-wrapper">
            <input
              class="activity__radio"
              type="radio"
              name="activity"
              id="high"
              value="1.725"
              v-model="activity"
            />
            <label class="activity__label" for="high"
              >Высокая
              <span>Тренировки 6-7 раз в неделю</span>
            </label>
          </div>
          <div class="activity__item-wrapper">
            <input
              class="activity__radio"
              type="radio"
              name="activity"
              id="highest"
              value="1.9"
              v-model="activity"
            />
            <label class="activity__label" for="highest"
              >Очень высокая
              <span>Больше 6 тренировок в неделю и физическая работа</span>
            </label>
          </div>
        </div>
      </div>

      <div class="calculation">
        <button class="calculation__submit" type="button" v-bind:disabled="calculate" v-on:click="countingCalories()">Рассчитать</button>
        <button class="calculation__reset" type="button" v-bind:disabled="reset" v-on:click="resetCounting()">
          Очистить поля и расчет
        </button>
      </div>
    </div>
    <div class="result" v-show="result">
      <h2 class="result__title">Ваша норма калорий</h2>
      <div class="result__inner">
        <div class="result__item">
          <div class="result__total">{{ normal }} ккал</div>
          <span>поддержание веса</span>
        </div>
        <div class="result__item">
          <div class="result__total">{{ loss }}  ккал</div>
          <span>снижение веса</span>
        </div>
        <div class="result__item">
          <div class="result__total">{{ gain }} ккал</div>
          <span>набор веса</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',

  data () {
    return {
      sex: 'male',
      age: '',
      height: '',
      weight: '',
      activity: 1.2,
      calculate: true,
      reset: true,
      result: false,
      normal: '',
      gain: '',
      loss: ''
    }
  },

  methods: {
    getNormalCalories () {
      let result = ''
      if (this.sex === 'male') {
        result = ((10 * this.weight) + (6.25 * this.height) - (5 * this.age) + 5) * this.activity
        // result = (88.362 + (13.397 * this.weight) + (4.799 * this.height) - (5.677 * this.age)) * this.activity
        return Math.round(result)
      }
      result = ((10 * this.weight) + (6.25 * this.height) - (5 * this.age) - 161) * this.activity
      // result = (447.593 + (9.247 * this.weight) + (3.098 * this.height) - (4.33 * this.age)) * this.activity
      return Math.round(result)
    },

    getGainCalories () {
      return Math.round(this.getNormalCalories() * 1.15)
    },

    getLossCalories () {
      return Math.round(this.getNormalCalories() * 0.85)
    },

    changeStateBtn () {
      if (this.weight && this.height && this.age) {
        this.calculate = false
        this.reset = false
      } else {
        this.calculate = true
        this.reset = true
      }
    },

    countingCalories () {
      this.normal = this.getNormalCalories()
      this.gain = this.getGainCalories()
      this.loss = this.getLossCalories()
      this.result = true
    },

    resetCounting () {
      this.sex = 'male'
      this.activity = 1.2
      this.age = ''
      this.height = ''
      this.weight = ''
      this.result = false
      this.changeStateBtn()
    }
  }

}
</script>

<style src="./assets/css/style.css"></style>
