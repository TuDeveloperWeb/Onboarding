<!-- App.vue -->
<template>
  <div id="app">
    <div class="container">
        <div class="target-area">
          <!-- Contenido de tu área específica -->
            <span> Hola Maria x ti voy a crear un Onboarding </span>
        </div>
  
        <div>

          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas viverra nunc sapien, non rhoncus elit tincidunt vitae. Vestibulum maximus, ligula eu feugiat molestie, massa diam imperdiet odio, vitae viverra ligula est id nisi. Aliquam ut molestie est. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Phasellus at consequat dui.
             Aenean tristique sagittis quam, sit amet sollicitudin neque sodales in.</p>

          <div class="d-flex justify-content-between">
              <b-card
                title="Card Title"
                img-src="https://picsum.photos/600/300/?image=25"
                img-alt="Image"
                img-top
                tag="article"
                style="max-width: 20rem;"
                class="mb-2 "
              >
                <b-card-text>
                  Some quick example text to build on the card title and make up the bulk of the card's content.
                </b-card-text>
            
                <b-button href="#" variant="primary">Go somewhere</b-button>
              </b-card>
            
              <b-card
                title="Card Title"
                img-src="https://picsum.photos/600/300/?image=25"
                img-alt="Image"
                img-top
                tag="article"
                style="max-width: 20rem;"
                class="mb-2 ml-2"
              >
                <b-card-text>
                  Some quick example text to build on the card title and make up the bulk of the card's content.
                </b-card-text>
            
                <b-button href="#" variant="primary">Go somewhere</b-button>
              </b-card>
            
              <b-card
                title="Card Title"
                img-src="https://picsum.photos/600/300/?image=25"
                img-alt="Image"
                img-top
                tag="article"
                style="max-width: 20rem;"
                class="mb-2 "
              >
                <b-card-text>
                  Some quick example text to build on the card title and make up the bulk of the card's content.
                </b-card-text>
            
                <b-button href="#" variant="primary">Go somewhere</b-button>
              </b-card>
          </div>


        </div>
    </div>
   
    <Onboarding
      v-if="showOnboarding"
      @closeOnboarding="closeOnboarding"
      :targetElement="targetElement"
    />
  </div>
</template>

<script>
import Onboarding from '@/components/Onboarding.vue';

export default {
  data() {
    return {
      showOnboarding: false,
      targetElement: null,
    };
  },

  mounted() {
    
    this.obtenerClass();
  },

  methods: {

    obtenerClass(){
        const targetElement = document.querySelector('.target-area');
        this.targetElement = targetElement;
        console.log(targetElement);

        if (this.targetElement ) {
            this.showOnboarding = true;
        }

    },
    openOnboarding(targetElement) {
      this.showOnboarding = true;
      this.targetElement = targetElement;
    },
    closeOnboarding() {
      this.showOnboarding = false;
      this.targetElement = null;
    },
    handleClick(event) {
      // Verificar si el clic ocurrió dentro del área específica
      const targetElement = event.target.closest('.target-area');
      console.log(targetElement);
      if (targetElement) {
        this.openOnboarding(targetElement);
      }
    },
  },
  components: {
    Onboarding,
  },
};
</script>

<style>
#app {
  text-align: center;
  margin-top: 60px;
}

.target-area {
  background-color: #e0e0e0;
  padding: 20px;
  margin: 20px;
  cursor: pointer;
}
</style>
