<template>
  <div id="page-forms">
    <v-container grid-list-xl fluid>
      <v-layout row wrap>
        <v-flex lg6>
          <v-card class="mb-4">
            <v-toolbar color="teal" dark flat dense cad>
              <v-toolbar-title class="subheading">Payment Form with validation</v-toolbar-title>
              <v-spacer></v-spacer>
            </v-toolbar>
            <v-divider></v-divider>
            <v-card-text class="">
              <payment-form></payment-form>
            </v-card-text>
          </v-card>
          <v-card>
            <v-toolbar color="success" dark flat dense cad>
              <v-toolbar-title class="subheading">Ship Form</v-toolbar-title>
              <v-spacer></v-spacer>
            </v-toolbar>
            <v-divider></v-divider>
            <v-card-text class="">
              <shipment-form></shipment-form>
            </v-card-text>
          </v-card>
        </v-flex>
        <v-flex lg6>
          <event-form></event-form>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import VWidget from '@/components/VWidget';
import ContactForm from '@/components/widgets/form/ContactForm';
import EventForm from '@/components/widgets/form/EventForm';
import PaymentForm from '@/components/widgets/form/PaymentForm';
import ShipmentForm from '@/components/widgets/form/ShipmentForm';

export default {
  components: {
    VWidget,
    ContactForm,
    PaymentForm,
    ShipmentForm,
    EventForm
  },
  data() {
    return {
      todo_items: [],
    };
  },
  computed: {},
  methods: {
    async send() {
      const item = await this.$axios.post('/api/todo', {
        title: 'teste',
        description: 'teste',
        done: false
      });
      this.todo_items.push(item);
    },

    list() {
      const items = this.$axios.get('/api/todo');
      this.todo_items = items;
    }
  }
};
</script>

<style lang="scss">

</style>
