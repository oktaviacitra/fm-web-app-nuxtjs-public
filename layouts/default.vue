<template>
  <v-app light>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item>
          <v-list-item-content>
            <img src="~/assets/monkey22.png" width="200">
          </v-list-item-content>
        </v-list-item>
        <v-divider />
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="title">
              PT. Money King Tbk.
            </v-list-item-title>
            <v-list-item-subtitle>
              Software
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-divider />
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <!-- <v-btn
        icon
        @click.stop="miniVariant = !miniVariant"
      >
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-btn
        icon
        @click.stop="clipped = !clipped"
      >
        <v-icon>mdi-application</v-icon>
      </v-btn> -->
      <!-- <v-btn
        icon
        @click.stop="fixed = !fixed"
      >
        <v-icon>mdi-minus</v-icon>
      </v-btn> -->
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-row class="fill-height" align="center" justify="center">
        <v-col cols="12">
          <v-autocomplete
            label="Search"
            :items="components"
          />
        </v-col>
      </v-row>
      <v-spacer />
      <div class="text-center">
        <v-menu offset-y>
          <template v-slot:activator="{ on }">
            <v-btn
              icon
              v-on="on"
            >
              <v-icon>mdi-bell</v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item
              v-for="(notification, index) in notifications"
              :key="index"
            >
              <v-row>
                <v-col cols="12">
                  <v-list-item-title>{{ notification.title }}</v-list-item-title>
                  <v-list-item-subtitle>{{ notification.subtitle }}</v-list-item-subtitle>
                </v-col>
              </v-row>
            </v-list-item>
          </v-list>
        </v-menu>
        <v-btn
          icon
          @click.stop="rightDrawer = !rightDrawer"
        >
          <v-icon>mdi-account</v-icon>
        </v-btn>
      </div>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-navigation-drawer
      v-model="rightDrawer"
      :right="right"
      temporary
      fixed
    >
      <v-list>
        <v-list-item two-line>
          <v-list-item-avatar>
            <img src="https://randomuser.me/api/portraits/women/81.jpg">
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title>Jane Smith</v-list-item-title>
            <v-list-item-subtitle>Logged In</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-divider />
        <v-list-item
          v-for="(account, i) in accounts"
          :key="i"
          :to="account.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ account.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-title v-text="account.title" />
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-footer
      :fixed="fixed"
      app
    >
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      notifications: [
        {
          title: 'Invoice',
          subtitle: 'Wifda paid the bill'
        },
        {
          title: 'Invoice',
          subtitle: 'Ega paid the bill'
        },
        {
          title: 'Invoice',
          subtitle: 'Macan paid the bill'
        }
      ],
      items: [
        // {
        //   icon: 'mdi-apps',
        //   title: 'Welcome',
        //   to: '/'
        // },
        // {
        //   icon: 'mdi-chart-bubble',
        //   title: 'Inspire',
        //   to: '/inspire'
        // },
        // {
        //   icon: 'mdi-account-circle',
        //   title: 'Test',
        //   to: '/dashboard/home'
        // }
        {
          icon: 'mdi-view-dashboard',
          title: 'Dashboard',
          to: '/feature/dashboard/'
        },
        {
          icon: 'mdi-file-presentation-box',
          title: 'Product',
          to: '/feature/product/'
        },
        {
          icon: 'mdi-coin',
          title: 'Payroll',
          to: '/feature/payroll/'
        },
        {
          icon: 'mdi-basket',
          title: 'Transaction',
          to: '/feature/transactions/'
        },
        {
          icon: '',
          title: 'Cash In',
          to: '/feature/transactions/cash-in/'
        },
        {
          icon: '',
          title: 'Cash Out',
          to: '/feature/transactions/cash-out/'
        },
        {
          icon: '',
          title: 'Debt & Loan',
          to: '/feature/transactions/debt-loan/'
        },
        {
          icon: 'mdi-note-text',
          title: 'Invoice',
          to: '/feature/invoice/'
        },
        {
          icon: 'mdi-glasses',
          title: 'Evaluation',
          to: '/feature/evaluation/'
        },
        {
          icon: 'mdi-newspaper',
          title: 'Report',
          to: '/feature/report/'
        }
      ],
      accounts: [
        {
          icon: 'mdi-account-circle',
          title: 'Profile',
          to: '/help/profile/'
        },
        {
          icon: 'mdi-settings',
          title: 'Setting',
          to: '/help/settings/'
        },
        {
          icon: 'mdi-book',
          title: 'Manual Book',
          to: '/help/manualbooks/'
        },
        {
          icon: 'mdi-comment-outline',
          title: 'Share Feedback',
          to: '/help/feedback/'
        },
        {
          icon: 'mdi-logout',
          title: 'Sign Out',
          to: '/help/signout/'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Money King',
      components: [
        'Autocompletes', 'Comboboxes', 'Forms', 'Inputs', 'Overflow Buttons', 'Selects', 'Selection Controls', 'Sliders', 'Textareas', 'Text Fields'
      ]
    }
  }
}
</script>
