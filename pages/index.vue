<template>
  <div class="container">
    <div>
      <div class="links">
        <nuxt-link
          class="button--green"
          :to="{
            name: 'index-section',
            params: {
              section: 'section-a',
            }
          }"
        >
          Section A
        </nuxt-link>
        <nuxt-link
          class="button--grey"
          :to="{
            name: 'index-section',
            params: {
              section: 'section-b',
            }
          }"
        >
          Section B
        </nuxt-link>
      </div>

      <transition name="section" mode="out-in">
        <nuxt-child />
      </transition>
    </div>
  </div>
</template>

<script>
export default {
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.links {
  margin-bottom: 15px;
}

/*
  In a Named Out-In Transition, we should target `.${transitionName}-{animationStep}`,
  for exemple, here: '.section-enter' to animate the transtion.

  This works fine with all the OUT animation steps ('leave', 'leave-active', 'leave-to')

  However with the IN animation steps ('enter', 'enter-active', 'leave-to') this fails
  because the injected class names uses the standard "page" transition name
*/

/* Uncomment this lines to make the transition work */
/* .page-enter-active, */
/* .page-leave-active, */
.section-enter-active,
.section-leave-active {
  transition: opacity 1s, transform 1s;
}

/* Uncomment this line to make the transition work */
/* .page-enter, */
.section-enter {
  opacity: 0;
  transform: translateX(-100%);
}
.section-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
</style>
