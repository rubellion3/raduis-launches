<template>
  <div class="column">
    <div class="card">
      <div class="card-content">
        <div class="level">
          <div class="level-left">
            {{ title }}
          </div>
          <div class="level-right">
            <div v-if="crew" class="level-item tag is-link">
              {{ crew + ' crew' }}
            </div>
            <div class="level-item" v-text="$moment(time).format('LLLL')"></div>
            <div v-if="upcoming" class="level-item">Upciming</div>
            <div v-if="success" class="level-item">Success</div>
          </div>
        </div>
      </div>
      <footer class="card-footer">
        <div class="card-footer-item">
          <span>
            <slot />
          </span>
        </div>
      </footer>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    upcoming: {
      type: Boolean,
    },
    success: {
      type: Boolean,
    },
    time: {
      type: String,
      required: true,
    },
    crew: {
      type: Number,
      required: true,
    },
    // icon: {
    //   type: String,
    //   required: true,
    // },
  },
}
</script>
