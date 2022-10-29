<template>
  <div>
    <v-app style="background : #f4f5f9" class="relative">
      <!----Start navigation drawer----------->
        <v-navigation-drawer v-model="drawer" app color="#2784ff" class="relative" mini-variant mini-variant-width="80px" right>
          <!------Start avatar------------->
          <v-avatar class="d-block text-center mx-auto mt-4 mb-16" size="40">
            <v-icon color="white" x-large>mdi-domain</v-icon>
          </v-avatar>
          <!------End avatar--------------->
          <!-----Start icons group in navigation------>
          <v-list class="mt-15">
            <v-list-item-group v-model="selectedItem">
              <v-list-item  v-for="icon in icons" :key="icon" active-class="border" class="mt-2" inactive :ripple="false">
                <v-icon color="white" class="d-flex">
                  {{icon.icon}}
                </v-icon>
              </v-list-item>
            </v-list-item-group>
          </v-list>
          <!-----End icons group in navigation------>
          <div class="bottom-controls">
            <v-icon dark class="d-block mb-4">
              mdi-wrench
            </v-icon>
            <v-icon dark  class="d-block">
              mdi-wrench
            </v-icon>
          </div>
        </v-navigation-drawer>
         <!----end navigation drawer------------>
         <!----Start navbar--------------------->
         <v-app-bar  app color="#01579B">
          <v-app-bar-nav-icon dark class="ml-1"></v-app-bar-nav-icon>
          <h4 class="white--text mx-3">کارت مریض</h4>
          <v-spacer></v-spacer>
          <h4 class="white--text">قرار ملاقات ها</h4>
          <v-icon x-smallb color="#fff" class="mx-2">mdi-download-outline</v-icon>
          <v-btn class="">
            <v-icon class="mx-2" color="#01579B">mdi-plus</v-icon>
          </v-btn>
          <v-badge dot overlap color="green" class="ml-3 mr-2">
            <v-avatar tile color="#e1f1f5" size="35">
              <v-icon size="18" color="#F4511E">mdi-bell</v-icon>
            </v-avatar>
          </v-badge>
         </v-app-bar>
         <!----End navabr----------------------->
      <v-main>
        <!----Start container ---->
        <v-container>
          <v-row>
            <v-col cols="12" sm="9">
              <v-row>
                <!---Start contact section---------->
                <v-col cols="12" sm="12">
                  <v-card color="white" class="mt-2" flat>
                    <v-row>
                      <v-col cols="12" sm="4">
                        <v-card color="#2784ff" class="rounded-lg px-2" flat>
                          <v-row>
                            <v-col cols="12" sm="4">
                              <v-avatar color="#dfedff" tile>
                                <v-img src="../assets/download.jpg"></v-img>
                              </v-avatar>
                            </v-col>
                            <v-col cols="12" sm="8">
                              <h4 class="white--text">پارسا فلاح نژاد</h4>
                              <h6 class="white--text">23 ساله</h6>
                            </v-col>
                            <v-col cols="12" sm="12" class="mt-3">
                             <v-row>
                              <v-col cols="12" sm="4">  
                                <h6 class="grey--text text--lighten-4">قد</h6>
                                <h6 class="white--text">180</h6>
                              </v-col>
                              <v-col cols="12" sm="4">  
                                <h6 class="grey--text text--lighten-4">وزن</h6>
                                <h6 class="white--text">60</h6>
                              </v-col>
                              <v-col cols="12" sm="4">  
                                <h6 class="grey--text text--lighten-4">گروه خونی</h6>
                                <h6 class="white--text">A+</h6>
                              </v-col>
                             </v-row>
                            </v-col>
                          </v-row>
                        </v-card>
                      </v-col>
                      <v-col cols="12" sm="3">
                        <v-card color="transparent" class="rounded-lg mx-2 px-2" flat>
                          <span class="caption grey--text mt-6">شماره تلفن</span>
                          <h5 class="black--text mb-7">989031613860</h5>
                          <span class="caption grey--text mt-6">شماره کارت</span>
                          <h5 class="black--text mb-7">13246598147</h5>
                        </v-card>
                      </v-col>
                      <v-col cols="12" sm="5">
                        <v-card color="transparent" class="rounded-lg mx-2 px-2" flat>
                          <span class="caption grey--text mt-6">آدرس ایمیل</span>
                          <h5 class="black--text mb-7">parsaddbb@gmail.com</h5>
                          <span class="caption grey--text mt-6">وضعیت پزشکی</span>
                          <h5 class="black--text mb-7">بیماری قلبی و عروقی</h5>
                        </v-card>
                      </v-col>
                    </v-row>
                  </v-card>
                </v-col>
                <!---End contact section---------->
                <!----Start table section--------->
                <v-col cols="12" sm="12">
                  <v-card>
                    <v-card-title>
                      <p class="text-h4 font-weight-medium mb-5">لیست کاربران</p>

                      <v-spacer></v-spacer>





                    <v-dialog v-model="dialog">
                      <template v-slot:activator="{ on, attrs }">
                        <v-btn color="primary" v-on="on" v-bind="attrs">
                          کاربر 
                          <v-icon class="mr-2">mdi-account-plus</v-icon>
                        </v-btn>
                      </template>

                      <v-card>
                        <v-card-title>
                          فرم کاربر جدید
                        </v-card-title>
                        <v-container>
                          <v-row>
                            <v-col cols="12" md="6" lg="4">
                              <v-text-field
                                label="نام"
                                v-model="userForm.name"
                              ></v-text-field>
                            </v-col>
                            <v-col cols="12" md="6" lg="4">
                              <v-text-field
                                label="ایمیل"
                                v-model="userForm.email"
                              ></v-text-field>
                            </v-col>
                            <v-col cols="12" md="6" lg="4">
                              <v-text-field
                                label="اسم کاربری"
                                v-model="userForm.username"
                              ></v-text-field>
                            </v-col>
                            <v-col cols="12" md="6" lg="4">
                              <v-select
                                v-model="userForm.gender"
                                :items="[
                                  { genderName: 'انتخاب جنسیت', genderCode: null },
                                  { genderName: 'مرد', genderCode: 1 },
                                  { genderName: 'زن', genderCode: 2 },
                                ]"
                                item-text="genderName"
                                item-value="genderCode"
                                label="جنسیت"
                                outlined
                              ></v-select>
                            </v-col>

                            <v-col cols="12" md="6" lg="4">
                            </v-col>


                            <v-col cols="12" md="6" lg="4" class="d-flex align-center">
                              <v-spacer></v-spacer>
                              <v-btn color="primary" @click="saveUser">ذخیره</v-btn>
                            </v-col>
                            
                          </v-row>
                        </v-container>
                      </v-card>

                    </v-dialog>

                      <v-text-field
                        class="mr-3"
                        label="جستجو در دیتا تیبل"
                        v-model="searchText"
                      ></v-text-field>
                    </v-card-title>

                    <v-data-table
                      :headers="titles"
                      :items="users"
                      :search="search"
                      no-results-text="هیچ کاربری برای مورد جستجو یافت نشد"
                      :footer-props="{
                        'items-per-page-text': 'تعداد ایتم در هر صفحه:'
                      }"
                    >
                      <template v-slot:[`item.name`]="{ item }">
                        {{ item.name.toUpperCase() }}
                      </template>
                      <template v-slot:[`item.gender`]="{ item }">
                        <v-chip
                          :color="item.gender === 1 ? 'blue' : 'pink'"
                          dark
                        >
                        {{ item.gender === 1 
                          ? 'مرد'
                          : 'زن'
                          }}
                        </v-chip>
                      </template>
                      <template v-slot:[`item.actions`]="{ item }">
                        <v-btn color="error" text @click="removeItem(item.id)">
                          <v-icon>mdi-delete</v-icon>
                        </v-btn>
                      </template>
                      <template v-slot:[`header.gender`]="{ header }">
                        <template v-if="header.text === 'جنسیت'">
                          <span>جنسیت</span>
                          <span class="mr-2 blue--text">(مرد/زن)</span>
                        </template>
                        <template v-else>{{ header.text }}</template>
                      </template>

                      <template v-slot:[`footer.page-text`]="{ pageStart, pageStop, itemsLength }">
                        {{ `از ${pageStart}-${pageStop} -- کل کابران (${itemsLength})` }}
                      </template>
                    </v-data-table>
                  </v-card>
                </v-col>
                <!----End table section------------>
              </v-row>
            </v-col>
            <v-col cols="12" sm="3">

            </v-col>
          </v-row>
        </v-container>
      </v-main>
    </v-app>
  </div>
</template>

<script>
export default {
data()
{
 return{
  //------start navabr data-------------//
  drawer : null,
  selectedItem : 3,
  icons : [
    {icon : 'mdi-message-text'},
    {icon : 'mdi-dialpad'},
    {icon : 'mdi-email'},
    {icon : 'mdi-call-split'},
    {icon : 'mdi-cloud-upload'},
  ],
  //---------End navnbr data------------//
  //----------start table data--------------//
  searchText: '',
    search: '',
    titles: [
      { text: 'اسم', value: 'name' },
      { text: 'ایمیل', value: 'email' },
      { text: 'اسم کاربری', value: 'username' },
      { text: 'جنسیت', value: 'gender' },
      { text: 'عملیات', value: 'actions' },
    ],
    users: [
      {
        id: 1,
        name: "Leanne Graham",
        username: "Bret",
        gender: 1,
        email: "Sincere@april.biz",
      },
      {
        id: 2,
        name: "Ervin Howell",
        username: "Antonette",
        gender: 2,
        email: "Shanna@gmail.com",
      },
      {
        id: 3,
        name: "Clementine Bauch",
        username: "Samantha",
        gender: 2,
        email: "Nathan@yesenia.net",
      },
      {
        id: 4,
        name: "Patricia Lebsack",
        username: "Karianne",
        gender: 2,
        email: "Julianne.OConner@kory.org",
      },
      {
        id: 5,
        name: "Chelsey Dietrich",
        username: "Kamren",
        gender: 2,
        email: "Lucio_Hettinger@gmail.com",
      },
      {
        id: 6,
        name: "Mrs. Dennis Schulist",
        username: "Leopoldo_Corkery",
        gender: 2,
        email: "Karley_Dach@gmail.com",
      },
      {
        id: 7,
        name: "Kurtis Weissnat",
        username: "Elwyn.Skiles",
        gender: 1,
        email: "Telly.Hoeger@billy.biz",
      },
      {
        id: 8,
        name: "Nicholas Runolfsdottir V",
        username: "Maxime_Nienow",
        gender: 1,
        email: "Sherwood@rosamond.me",
      },
      {
        id: 9,
        name: "Glenna Reichert",
        username: "Delphine",
        gender: 1,
        email: "Chaim_McDermott@dana.io",
      },
      {
        id: 10,
        name: "Clementina DuBuque",
        username: "Moriah.Stanton",
        gender: 2,
        email: "Rey.Padberg@karina.biz",
      }
    ],
    userForm: {
      name: '',
      email: '',
      username: '',
      gender: null
    },
    dialog: false
   //--------End table data-----------------//
 } 
},
watch: {
    searchText(newValue) {
      if (newValue === 'مرد') {
        this.search = "1";
        return;
      } else if (newValue === 'زن') {
        this.search = "2";
        return;
      }
      this.search = newValue
    }
  },
  methods: {
    saveUser() {
      this.dialog = false;
      const id = Math.random();
      this.users.push({ id, ...this.userForm })
      this.userForm = {
        name: '',
        email: '',
        username: '',
        gender: null
      }
    },
    removeItem(id) {
      this.users = this.users.filter(user => user.id !== id)
    }
  },
}
</script>

<style>
.border
{
  width : 60%;
  margin: 0 auto;
  background: #529dff;
  border-radius: 50%;
}
.bottom-controls
{
  position: absolute;
  bottom: 20px;
  left : 50%;
  transform: translateX(-50%);
}
</style>