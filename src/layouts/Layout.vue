<script setup lang="ts">
import ClassicTheme from "@/layouts/themes/ClassicTheme.vue"
import TopBLayout from "@/layouts/themes/TopBLayout.vue"
import { useSettingStore } from "@/store"
import { useGetBreadcrumbList } from "@/utils/public/getData"
const settingStore = useSettingStore()
useGetBreadcrumbList() // 监听路由获取面包屑
</script>

<template>
	<div class="container_layout">
		<Transition name="fade-transform">
			<template v-if="settingStore.layoutTheme == 'classic'">
				<ClassicTheme />
			</template>
			<template v-else-if="settingStore.layoutTheme == 'topb'">
				<TopBLayout />
			</template>
		</Transition>
	</div>
</template>

<style lang="scss" scoped>
.container_layout {
	display: flex;
	width: 100%;
	height: 100%;
}

.fade-transform-enter-active,
.fade-transform-leave-active {
	transition: all 0.3s;
}

.fade-transform-enter-from,
.fade-transform-leave-to {
	opacity: 0;
}

.fade-transform-leave-active {
	position: absolute;
}

.fade-transform-enter-active {
	position: absolute;
}
</style>
