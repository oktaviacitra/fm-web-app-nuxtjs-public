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
            <v-list-item-title class="title">
              Application
            </v-list-item-title>
            <v-list-item-subtitle>
              subtext
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>
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
      label="Components"
      :items="components"
    ></v-autocomplete>
      </v-col>
</v-row>
      <v-spacer />
      <v-btn
        icon
        @click.stop="rightDrawer = !rightDrawer"
      >
        <v-icon>mdi-account</v-icon>
      </v-btn>
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
        <v-divider></v-divider>
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
          to: '/dashboard/home'
        },
        {
          icon: 'mdi-file-presentation-box',
          title: 'Product',
          to: '/dashboard/product'
        },
        {
          icon: 'mdi-coin',
          title: 'Payroll',
          to: '/dashboard/payroll'
        },
        {
          icon: 'mdi-basket',
          title: 'Transaction',
          to: '/dashboard/transaction',
          items: [
            {
              title: 'Cash In'
            },
            {
              title: 'Cash Out'
            },
            {
              title: 'Debt & Loan'
            }
          ]
        },
        {
          icon: 'mdi-note-text',
          title: 'Invoice',
          to: '/dashboard/invoice'
        },
        {
          icon: 'mdi-glasses',
          title: 'Evaluation',
          to: '/dashboard/evaluation'
        },
        {
          icon: 'mdi-newspaper',
          title: 'Report',
          to: '/dashboard/report'
        }
      ],
      accounts: [
        {
          icon: 'mdi-account-circle',
          title: 'Profile',
          to: '/dashboard/profile'
        },
        {
          icon: 'mdi-settings',
          title: 'Setting',
          to: '/dashboard/setting'
        },
        {
          icon: 'mdi-book',
          title: 'Manual Book',
          to: '/dashboard/manualbook'
        },
        {
          icon: 'mdi-comment-outline',
          title: 'Share Feedback',
          to: '/dashboard/feedback'
        },
        {
          icon: 'mdi-logout',
          title: 'Sign Out',
          to: '/dashboard/signout'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Money King',
      components: [
          'Autocompletes', 'Comboboxes', 'Forms', 'Inputs', 'Overflow Buttons', 'Selects', 'Selection Controls', 'Sliders', 'Textareas', 'Text Fields',
        ]
    }
  }
}
</script>
