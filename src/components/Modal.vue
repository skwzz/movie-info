<template>
    <div v-if="isModal" class="modal">
        <div class="inner">
            <h3>{{this.data[selectedMovie].title}}</h3>
            <p>영화 상세보기</p>
            <button @click="isModal=false">닫기</button>
        </div>
    </div>
</template>
<script>
export default {
    name: "ModalComponent"
}
</script>
<style>
    
</style>