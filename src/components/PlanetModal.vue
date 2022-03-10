<template>
  <div class="modal">
    <div class="modal__box">
      <h1 class="modal__title">
        {{ planetName }}
      </h1>
      <button
        class="modal__close"
        @click="close"
      >
        X
      </button>
      <iframe
        class="modal__video"
        :src="videoLink"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      />
      <a
        rel="noopener noreferrer"
        target="_blank"
        class="modal__link"
        :href="wikipedia"
      >Wikipédia</a>
    </div>
    <div class="modal__backdrop" />
  </div>
</template>

<script>
export default {
  name: 'PlanetModal',
  props: {
    // eslint-disable-next-line vue/require-default-prop
    videoLink: {
      type: String,
      reqired: true
    },
    planetName: {
      type: String,
      required: true
    },
    wikipedia: {
      type: String,
      required: true
    }
  },
  methods: {
    close() {
      this.$emit('close');
    },
  },
};
</script>

<style lang="scss" scoped>
h1 {
  margin: 0;
}
.modal {
  position: fixed;
  width: 100%;
  height: 100%;
  z-index: 9999;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  &__backdrop {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    z-index: 50;
  }
  &__box {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 80%;
    height: 80%;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  &__video {
    width: 100%;
    height: 100%;
    border-radius: 5px;
    border: 2px solid white;
  }

  &__title {
    color: #fff;
    position: absolute;
    top: -10%;
    left: 0;
  }
  &__close {
    position: absolute;
    top: -10%;
    right: 0;
    background: none;
    border: none;
    color: #fff;
    font-size: 2rem;
    cursor: pointer;
    font-weight: bold;
  }

  &__link {
    position: absolute;
    bottom: -7%;
    left: 0;
    background: none;
    border: none;
    color: #c6c6c6;
    font-size: 1rem;
    cursor: pointer;

    &:hover {
      border-bottom: 1px solid #c6c6c6;
    }
  }
}
</style>
