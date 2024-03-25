<template>
  <div class="wrapper q-py-lg">
    <h1 class="text-h6 q-my-none second-font">РЕКВИЗИТЫ</h1>

    <div class="row q-py-lg">
      <div class="col">
        <div class="row q-col-gutter-lg justify-center">
          <div>
            <q-table
              :rows="requisits"
              :columns="columns"
              flat
              bordered
              :rows-per-page-options="[0]"
              hide-bottom
              class="second-font text-body2"
            />

            <a
              href="https://drive.google.com/file/d/1WxNIZ3wvSqvfPgAgqx0miw1YI6ko7hVP/view?usp=sharing"
              target="_blank"
              class="q-mt-md text-center text-weight-bold cursor-pointer"
              style="display: block; color: black; text-decoration: none"
            >
              Скачать pdf файл с реквизитами
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      columns: [
        { align: "left", field: "name", classes: "text-weight-bold" },
        { align: "left", field: "data" },
      ],
      requisits: [
        {
          name: "Наименование",
          data: "Общество с ограниченной ответственностью «ГЕОМЕТРИЯ»",
        },
        {
          name: "ИНН",
          data: "2311347376",
        },
        {
          name: "КПП",
          data: "231101001",
        },
        {
          name: "ОГРН",
          data: "1232300017938",
        },
        {
          name: "Дата регистрации",
          data: "29.03.2023г",
        },
        {
          name: "Юридический адрес",
          data: "350028, Краснодарский край, г. Краснодар, ул. им. Жлобы, д. 139 ,кв. 135",
        },
        {
          name: "Расчетный счет",
          data: "40702810410001354008",
        },
        {
          name: "Наименование банка",
          data: "АО «ТИНЬКОФФ БАНК»",
        },
        {
          name: "Корреспондентский счет",
          data: "30101810145250000974",
        },
        {
          name: "БИК",
          data: "044525974",
        },
        {
          name: "Телефон",
          data: "+7-928-333-23-90",
        },
        {
          name: "Эл. почта ",
          data: "sk.geo.sk@mail.ru",
        },
        {
          name: "Генеральный директор",
          data: "Полищук  Сергей Васильевич",
        },
      ],
    };
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
::v-deep(.q-table thead) {
  display: none !important;
}
</style>
