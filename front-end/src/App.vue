  <template>
  <div id="nav">
    <b-navbar toggleable="md" type="dark" variant="info">
      <b-navbar-brand href="/">Accueil</b-navbar-brand>
      <b-collapse is-nav id="nav_collapse">
        <b-navbar-nav>
          <b-nav-item-dropdown text="Liste">
            <b-dropdown-item href="/campus">Campus</b-dropdown-item>
          </b-nav-item-dropdown>
          <b-nav-item href="/stat">Statistiques</b-nav-item>
        </b-navbar-nav>
        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input size="sm" class="mr-sm-2" type="text" placeholder="Recherche"/>
            <b-button size="sm" class="my-2 my-sm-0" type="submit">Recherche</b-button>
          </b-nav-form>
          <b-nav-item-dropdown right>
            <!-- Using button-content slot -->
            <template slot="button-content">
              <em>Utilisateur</em>
            </template>
            <b-dropdown-item @click.stop="logout" href="">Déconnexion</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>

    <router-view></router-view>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data () {
    return {}
  },
  mounted() {
    axios.get('http://localhost:3000/login').then(result => {
      if(!result) {
        this.$router.replace({ name: "login" });
      }
    });
  },
  methods: {
    logout() {
        axios.post('http://localhost:3000/logout');
    }
  }
}
</script>

<style scoped>
</style>