<template>
  <div>
    <div class="accordion">
	<div
		class="accordion-item"
		v-for="(content, i) in contents" 
    v-bind:key="i"
		:class="{ 'accordion-active': content.active }"
	>
		<div class="accordion-header">
			<a href="#" @click="expand(i)">
				<div class="accordion-header-div">{{ content.title }}</div>
				<div class="accordion-header-div">
					<div class="accordion-caret"></div>
				</div>
			</a>
		</div>
		<div class="accordion-body" v-bind:ref="'accordion-body-' + i">
			<div class="accordion-content">{{ content.description }}</div>
		</div>
	</div>
</div>
  </div>
</template>

<script>
import {TweenLite,Bounce,Elastic } from 'gsap'

export default {
  name: "Accordion",
	data () {
		return {
      contents: [
        {
			title: 'Lorem ipsum dolor sit amet',
			description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
			active: false
      }, 
      {
			title: 'Ut enim ad minim veniam',
			description: 'Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
			active: false
		}, {
			title: 'Duis aute irure dolor in reprehenderit',
			description: 'Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur',
			active: false
		}, {
			title: 'Excepteur sint occaecat cupidatat non proident',
			description: 'Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.',
			active: false
		}]
		}
  },
  methods: {
		expand (i) {
			// e.preventDefault();

			let el = this.$refs['accordion-body-' + i][0];

			if (this.contents[i].active === false) {
				this.contents[i].active = true;

				TweenLite.to(el, 1, {
					height: el.scrollHeight,
					ease: Elastic.easeOut.config(1, 0.3)
				});
			} else {
				this.contents[i].active = false;
				TweenLite.to(el, 0.5, {
					height: 0,
					ease: Bounce.easeOut
				});
			}
		}
	}
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.accordion {
  background-color: #ffffff;
  width: 100%;
  max-height: 100%;
  max-width: 320px;
  padding: 2rem 1rem;
  margin: auto;
  box-sizing: border-box;
  overflow: auto;
  box-shadow: 0 0.5rem 1rem rgba(0, 0, 0, 0.3);
}

.accordion-item.accordion-active .accordion-caret {
  animation: accordion-is-active 200ms linear forwards;
}

.accordion-header {
  color: inherit;
  font-size: 1.2rem;
  font-weight: bold;
  position: relative;
}
.accordion-header a {
  color: inherit;
  text-decoration: none;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: space-between;
  box-sizing: border-box;
  border-radius: 0.6rem;
  transition: background-color 200ms ease-in-out;
}
.accordion-header a:not(.accordion-active):hover {
  background-color: #efefef;
}

.accordion-header-div {
  padding: 1rem 1rem 1rem 1rem;
}
.accordion-header-div:last-child {
  padding-left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.accordion-caret {
  background-image: linear-gradient(to top right, transparent 50%, #727272 50%);
  width: 0.5rem;
  height: 0.5rem;
  transform: rotate(-45deg);
  animation: accordion-is-inactive 200ms linear forwards;
}

.accordion-body {
  height: 0;
  overflow: hidden;
}

.accordion-content {
  padding: 1rem;
}

@keyframes accordion-is-inactive {
  0% {
    transform: rotate(-45deg);
  }
  50% {
    transform: scale(1.5) rotate(45deg);
  }
  100% {
    transform: rotate(135deg);
  }
}
@keyframes accordion-is-active {
  0% {
    transform: rotate(135deg);
  }
  50% {
    transform: scale(1.5) rotate(45deg);
  }
  100% {
    transform: rotate(-45deg);
  }
}
@media screen and (min-width: 320px) {
  #app {
    padding: 2rem;
    overflow: auto;
  }

  .accordion {
    max-height: none;
    border-radius: 0.5rem;
  }
}

</style>
