<template>
  <div class="column">
    <div class="card">
      <div class="card-content">
        <div class="level">
          <div class="level-left">
            <div class="level-item">
              <b-image
                :src="
                  icon
                    ? icon
                    : 'https://cdn.dribbble.com/users/610788/screenshots/5157282/spacex.png?compress=1&resize=48x48'
                "
                rounded
                class="is-48x48"
              ></b-image>
            </div>
            <div class="level-item">{{ title }}</div>
          </div>
          <div class="level-right">
            <div v-if="crew" class="level-item tag is-link">
              {{ crew + ' crew' }}
            </div>
            <div
              class="level-item"
              v-text="$moment(time).format('dddd LL')"
            ></div>
            <div v-if="upcoming" class="level-item has-text-link-dark">
              Upciming
            </div>
            <div v-if="success" class="level-item">Success</div>
          </div>
        </div>
      </div>
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
    icon: {
      type: String,
      default: '',
    },
  },
}
</script>
