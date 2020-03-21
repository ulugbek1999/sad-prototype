<template>
  <div>
    <div class="display-1 text-center mb-5 font-weight-bold">
      List of customers
    </div>
      <v-data-table
        v-model="selected"
        :headers="headers"
        :items="desserts"
        :single-select="singleSelect"
        item-key="name"
        show-select
        class="elevation-1"
      >
      <template v-slot:top>
        <v-switch v-model="singleSelect" label="Single select" class="pa-3"></v-switch>
      </template>
    </v-data-table>
  </div>

</template>

<script>
  export default {
    layout: "dashboard",
    head() {
      return {
        title: "List of customers"
      };
    },
    data () {
      return {
        singleSelect: false,
        selected: [],
        headers: [
          {
            text: 'Full name',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Email', value: 'email' },
          { text: 'Phone number', value: 'phone' },
          { text: 'Registered date', value: 'created_at' },
        ],
        desserts: [
          {
            name: 'Rustam Turgunov',
            email: 'rustam.turgunov@gmail.com',
            phone: "+998909167516",
            created_at: "12 November 2019",
          },
          {
            name: 'Nodir Shuxratov',
            email: 'nodir.shuxratov@gmail.com',
            phone: "+998913234312",
            created_at: "13 December 2020",
          },
          {
            name: 'Zafar Yuldoshev',
            email: 'zafar.yuldoshev@gmail.com',
            phone: "+998903214324",
            created_at: "13 December 2020",
          },
          {
            name: 'Mamur Kodirov',
            email: 'mamur.kodirov@gmail.com',
            phone: "+998902122121",
            created_at: "18 August 2015",
          },
          {
            name: 'Islom Nazarov',
            email: 'islom.nazarov@gmail.com',
            phone: "+998901232332",
            created_at: "01 September 2017",
          },
          {
            name: 'Nurali Uktamov',
            email: 'nurali.uktamov@gmail.com',
            phone: "+998924324387",
            created_at: "25 December 2020",
          },
          {
            name: 'Sanjar Akhmedov',
            email: 'sanjar.akhmedov@gmail.com',
            phone: "+998924324387",
            created_at: "17 November 2019",
          },
          {
            name: 'Khotamjon Ketmonov',
            email: 'khotamjon.ketmonov@gmail.com',
            phone: "+998907564311",
            created_at: "23 March 2020",
          },
          {
            name: 'Iroda Nazarova',
            email: 'iroda.nazarova@gmail.com',
            phone: "+998907564311",
            created_at: "31 March 2020",
          },
          {
            name: 'Iosif Stalin',
            email: 'iosif.stalin@gmail.com',
            phone: "+998924325465",
            created_at: "23 June 2019",
          },
          {
            name: 'Jakhongir Ruziyev',
            email: 'jakhongir.ruziyev@gmail.com',
            phone: "+998913242121",
            created_at: "10 July 2020",
          },
          {
            name: 'Sanjar Akhmedov',
            email: 'sanjar.akhmedov@gmail.com',
            phone: "+998924324387",
            created_at: "17 November 2019",
          },
          {
            name: 'Zafar Yuldoshev',
            email: 'zafar.yuldoshev@gmail.com',
            phone: "+998903214324",
            created_at: "13 December 2020",
          },
           {
            name: 'Nodir Shuxratov',
            email: 'nodir.shuxratov@gmail.com',
            phone: "+998913234312",
            created_at: "13 December 2020",
          },
        ],
      }
    },
  }
</script>