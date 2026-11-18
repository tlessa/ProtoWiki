<script setup lang="ts">
import { CdxButton, CdxIcon } from '@wikimedia/codex'
import { cdxIconEllipsis } from '@wikimedia/codex-icons'

import gameImageUrl from './assets/fun-space-game.png'
import paginationUrl from './assets/fun-space-pagination.svg'

/** Placeholder games from the Figma "For you tab" frame (node 14044:5673). */
const games = [
  { id: 1, title: 'Game #1' },
  { id: 2, title: 'Game #2' },
  { id: 3, title: 'Game #3' },
]
</script>

<template>
  <section
    class="fun-space"
    aria-labelledby="fun-space-title"
  >
    <div class="fun-space__content">
      <div class="fun-space__title-row">
        <h2
          id="fun-space-title"
          class="fun-space__title"
        >
          Fun Space
        </h2>
        <CdxButton
          weight="quiet"
          aria-label="More options"
        >
          <CdxIcon :icon="cdxIconEllipsis" />
        </CdxButton>
      </div>

      <ul class="fun-space__games">
        <li
          v-for="game in games"
          :key="game.id"
          class="fun-space__card"
        >
          <div class="fun-space__card-body">
            <p class="fun-space__card-title">
              {{ game.title }}
            </p>
            <CdxButton class="fun-space__play">
              Play today’s game
            </CdxButton>
          </div>
          <img
            class="fun-space__card-image"
            :src="gameImageUrl"
            alt=""
            draggable="false"
          >
        </li>
      </ul>
    </div>

    <div class="fun-space__pagination">
      <img
        :src="paginationUrl"
        width="28"
        height="8"
        alt=""
      >
    </div>
  </section>
</template>

<style scoped>
/* Fills one story slot of the For you feed. ForYouFeed's header + tabs
   float over the top, so content starts below them. */
.fun-space {
  position: relative;
  height: 100%;
  overflow: hidden;
  background-color: #196551;
  background-image: linear-gradient(to top, rgba(0, 0, 0, 0) 68.2%, rgba(0, 0, 0, 0.6) 90.6%);
  color: #f8f9fa;
}

.fun-space__content {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-100, 16px);
  padding: 132px var(--spacing-100, 16px) 0;
}

.fun-space__title-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: var(--spacing-50, 8px);
}

.fun-space__title {
  margin: 0;
  min-width: 0;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  font-family: var(--font-family-serif);
  font-size: var(--font-size-xx-large, 1.5rem);
  font-weight: var(--font-weight-normal, 400);
  line-height: 32px;
  color: #f8f9fa;
}

.fun-space__title-row .cdx-button {
  flex-shrink: 0;
  color: #f8f9fa;
}

.fun-space__games {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin: 0;
  padding: 0;
  list-style: none;
}

.fun-space__card {
  display: flex;
  justify-content: space-between;
  gap: var(--spacing-100, 16px);
  height: 140px;
  box-sizing: border-box;
  padding: var(--spacing-100, 16px);
  border-radius: 16px;
  background-color: #202122;
  overflow: hidden;
}

.fun-space__card-body {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 21px;
  min-width: 0;
}

.fun-space__card-title {
  margin: 0;
  color: #eaecf0;
  font-size: var(--font-size-medium, 0.875rem);
  line-height: 20px;
  letter-spacing: 0.25px;
}

/* Outlined pill — only the delta from Codex's default button. */
.fun-space__play.cdx-button {
  min-height: 0;
  padding: 10px var(--spacing-100, 16px);
  border: var(--border-width-base, 1px) solid #f8f9fa;
  border-radius: 100px;
  background-color: transparent;
  color: #f8f9fa;
  font-size: var(--font-size-medium, 0.875rem);
  font-weight: 500;
  line-height: 20px;
  letter-spacing: 0.1px;
}

.fun-space__play.cdx-button:hover {
  background-color: rgba(248, 249, 250, 0.08);
}

.fun-space__play.cdx-button:active {
  background-color: rgba(248, 249, 250, 0.16);
}

.fun-space__card-image {
  flex-shrink: 0;
  width: 100px;
  height: 100px;
  border-radius: 12px;
  object-fit: cover;
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.15);
}

.fun-space__pagination {
  position: absolute;
  inset-inline: 0;
  bottom: var(--spacing-50, 8px);
  display: flex;
  justify-content: center;
  pointer-events: none;
}

.fun-space__pagination img {
  display: block;
}
</style>
