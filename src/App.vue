<template>
  <div>
    <LocalSwitcher />
    <FullScreen id="main" />
    <About id="about" />
    <Solution id="solution" />
    <Needs id="garden-needs" />
    <Start id="start" />
    <Points />
    <!-- <Impact id="impact" /> -->
    <!-- <Support id="support" /> -->
    <!-- <BrownCards /> -->
    <Development id="development" />
    <Activities id="resources" />
    <Partners id="partners" />
    <Sponsors />
    <Contacts />
    <Footer />
  </div>
</template>

<script>
import LocalSwitcher from "./components/LocalSwitcher.vue";
import About from "./components/About.vue";
import FullScreen from "./components/FullScreen.vue";
import Solution from "./components/Solution.vue";
import Needs from "./components/Needs.vue";
import Points from "./components/Points.vue";
import Start from "./components/Start.vue";
import Impact from "./components/Impact.vue";
import Support from "./components/Support.vue";
import BrownCards from "./components/BrownCards.vue";
import Development from "./components/Development.vue";
import Activities from "./components/Activities.vue";
import Partners from "./components/Partners.vue";
import Sponsors from "./components/Sponsors.vue";
import Contacts from "./components/Contacts.vue";
import Footer from "./components/Footer.vue";
export default {
  components: {
    LocalSwitcher,
    FullScreen,
    About,
    Solution,
    Needs,
    Start,
    Points,
    Impact,
    Support,
    BrownCards,
    Development,
    Activities,
    Partners,
    Sponsors,
    Contacts,
    Footer,
  },
};
</script>
