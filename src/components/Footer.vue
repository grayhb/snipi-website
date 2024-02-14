<template>
  <v-footer padless class="snipi-footer">
    <v-container>
      <v-row>
        <v-col cols="12" md="6">
          <div><b>8 (846) 205-86-00</b></div>
          <div class="footer-subtitle mb-2">Городской телефон</div>
          <a href="mailto:snipioil@samnipi.rosneft.ru">
            <v-icon color="yellow accent-4" class="mr-2 footer-mail-icon">mdi-email</v-icon
            >SNIPIOIL@SAMNIPI.ROSNEFT.RU</a
          >
        </v-col>
        <v-col cols="12" md="6">
          <div class="d-flex">
            <div>
              Юридический адрес: <br />
              443010, Российская Федерация, <br />
              г. Самара, ул. Вилоновская, д.18.
            </div>
            <div class="ml-6">
              ИНН: 6316058992<br />
              КПП: 631501001<br />
              ОГРН: 1026301159939
            </div>
          </div>
        </v-col>

        <v-col cols="12" class="py-0">
          <v-divider color="grey"></v-divider>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" md="6">
          <div class="d-flex align-center">
            <span
              class="footer-company-name"
              title="Общество с ограниченной ответственностью «Самарский научно-исследовательский и проектный институт нефтедобычи»"
            >
              © СамараНИПИнефть,
              {{ new Date().getFullYear() }}
            </span>
            <div class="ml-2">
              Мы в соцсетях:
              <v-btn href="https://vk.com/samaranipioil" target="_blank" class="" icon>
                <v-img src="@/assets/img/vk-icon.svg" max-height="28" max-width="28"></v-img>
              </v-btn>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-footer>
</template>

<script>
import { SITE } from '../configs/const'

export default {
  computed: {
    pages() {
      return SITE.pages
    }
  }
}
</script>

<style scoped>
.snipi-footer {
  border-top: 5px solid #fecf00;
  background-color: #5a5b5d;
  color: #eee;
  font-size: 0.9rem;
}

.snipi-footer a {
  color: #fad646;
}

.footer-subtitle {
  font-size: 0.7rem;
  color: #aaa;
}

.footer-company-name {
  font-size: 0.9rem;
  color: #fad646;
}

@media only screen and (max-width: 600px) {
  .snipi-footer,
  .footer-company-name {
    font-size: 0.7rem;
  }

  .footer-mail-icon {
    display: none;
  }

  .snipi-footer {
    padding-bottom: 64px;
  }
}
</style>
