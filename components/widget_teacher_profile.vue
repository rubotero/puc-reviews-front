<template>
  <v-card
  :loading="teacher.length == 0"
  class="mx-auto"
  :width="width"
  scrollable>
        <v-card-title class="headline grey lighten-2 mb-2">
          {{ teacher.name }}
        </v-card-title>

        <v-card-text>
          <v-row >
        <!-- COLUMNA Atributos -->
            <v-col
            cols="4">
              <h5>Detalles</h5>
              <v-divider></v-divider>
              <v-row>
                 <h6><v-icon>mdi-star</v-icon> {{ teacher.global_rating }}</h6>
              </v-row>
              <v-row>
                 <h6><v-icon>mdi-email</v-icon> {{ teacher.email }}</h6>
              </v-row>
              <v-row>
                 <h6><v-icon>mdi-notebook</v-icon> Ramos</h6>
                <b-table
                :items="teacher.courses"
                :fields="coursesFields">
                </b-table>
              </v-row>
            </v-col>
        <!-- COLUMNA REVIEWS -->
            <v-col
            >
              <widget_review_list :reviews="teacher_reviews"></widget_review_list>
            </v-col>
          </v-row>
        </v-card-text>
      </v-card>
</template>

<script>
import widget_review_list from "@/components/widget_review_list.vue"

export default {
  components: {
    widget_review_list
  },
  props: {
    teacher: {
      type: Object,
      default() {
        return {}
      }
    },
    teacher_reviews: {
      type: Array,
      default() {
        return []
      }
    },
    width: {
      type: String,
      default: "800"
    }
  },
  methods: {

    },
  data() {
    return {
      coursesFields: [
          {
            key: 'name',
            label: 'Nombre',
            sortable: true,
          },
      ]
    }
  }
}
</script>

<style>

</style>