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
            />
            <label class="activity__label" for="highest"
              >Очень высокая
              <span>Больше 6 тренировок в неделю и физическая работа</span>
            </label>
          </div>
        </div>
      </div>

      <div class="calculation">
        <button class="calculation__submit" type="button">Рассчитать</button>
        <button class="calculation__reset" type="button">
          Очистить поля и расчет
        </button>
      </div>
    </div>
    <div class="result">
      <h2 class="result__title">Ваша норма калорий</h2>
      <div class="result__inner">
        <div class="result__item">
          <div class="result__total">4545 ккал</div>
          <span>поддержание веса</span>
        </div>
        <div class="result__item">
          <div class="result__total">3434 ккал</div>
          <span>снижение веса</span>
        </div>
        <div class="result__item">
          <div class="result__total">2233 ккал</div>
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
      one: ''
    }
  }
}
</script>

<style src="./assets/css/style.css"></style>
