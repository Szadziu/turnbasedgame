<template>
  <div v-if="char.currentHealth" class="card" :class="{ dead: heroDead }">
    <div class="card__image">
      <img :src="char.image" :alt="char.name" />
    </div>

    <div v-if="char.level" class="card__level">level {{ char.level }}</div>
    <div v-else class="card__level">hero</div>

    <div class="card__name">{{ char.name }}</div>

    <HealthBar color="#42B782" v-model="percentageValue" />

    <div class="card__stats">
      <div class="one-third" :class="`one-third--${char.name}`">
        <div class="stat">HP</div>
        <div class="stat-value">{{ char.currentHealth }}</div>
      </div>

      <div class="one-third" :class="`one-third--${char.name}`">
        <div class="stat">Combat</div>
        <div class="stat-value">{{ char.combatEfficiency }}</div>
      </div>

      <div class="one-third" :class="`one-third--${char.name}`">
        <div class="stat">Magic</div>
        <div class="stat-value">{{ char.magicKnowledge }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import HealthBar from './HealthBar';

export default {
  name: 'CharacterCard',
  components: {
    HealthBar,
  },
  props: ['char'],
  computed: {
    percentageValue() {
      if (this.heroDead) return 0;
      return (this.char.currentHealth * 100) / this.char.maxHealth;
    },
    heroDead() {
      return this.char.currentHealth <= 0;
    },
  },
};
</script>

<style lang="scss" scoped>
@import '@/scss/variables.scss';


.dead {
  filter: grayscale(1);
}

.card {
  background: white;
  width: 300px;
  display: inline-block;
  margin: auto;
  border-radius: $border-radius-size + 5;
  position: relative;
  text-align: center;
  box-shadow: -1px 15px 30px -12px black;

  &__image {
    position: relative;
    height: 230px;
    margin-bottom: 35px;
    border-top-left-radius: $border-radius-size;
    border-top-right-radius: $border-radius-size;
    img {
      width: 90%;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  }

  &__level {
    text-transform: uppercase;
    font-size: 14px;
    font-weight: 700;
    margin-bottom: 3px;
  }

  &__name {
    font-size: 26px;
    color: black;
    font-weight: 900;
    margin-bottom: 5px;
    text-transform: uppercase;
  }

  &__stats {
    display: flex;
    font-weight: 700;
    border-bottom-left-radius: $border-radius-size;
    border-bottom-right-radius: $border-radius-size;
    overflow: hidden;

    .one-third {
      width: 33%;
      background-color: $barbarian;
      color: white;
      padding: 20px 15px;
      box-sizing: content-box;

      &--viking {
        background-color: $barbarian;
      }

      &--wizard {
        background-color: $wizard;
      }

      &--rogue {
        background-color: $rogue;
      }
      &--knight {
        background-color: $knight;
      }
      &--druid {
        background-color: $druid;
      }

      &--imp {
        background-color: $imp;
      }
      &--giant {
        background-color: $giant;
      }
      &--harpy {
        background-color: $harpy;
      }
      &--reaper {
        background-color: $reaper;
      }
      &--vampire {
        background-color: $vampire;
      }

      &--gnome {
        background-color: $gnome;
      }

      &--goblin {
        background-color: $goblin;
      }

      &--dragon {
        background-color: $dragon;
      }

      &--troll {
        background-color: $troll;
      }

      &--ogre {
        background-color: $ogre;
      }
    }

    .one-third:nth-child(even) {
      border-left: 2px solid rgba(0, 0, 0, 0.3);
      border-right: 2px solid rgba(0, 0, 0, 0.3);
    }
    .stat {
      text-transform: uppercase;
      font-weight: 400;
      font-size: 12px;
      margin-bottom: 10px;
    }

    .stat-value {
      position: relative;
      font-size: 28px;
    }
  }
}
</style>