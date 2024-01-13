<template>
    <div>
        <h3>--------computed without vuex--------</h3>
        <!-- <p>Raduis: {{ raduis }}</p> -->
        <p>Raduis: {{ raduis }}</p>
        <p>Circle's Area: {{ area }}</p>
        <button @click="increaseRaduis">Increase Raduis</button>
        <button @click="decreaseRaduis">Decrease Raduis</button>
    </div>
</template>

<script>
import { ref, reactive, computed, toRefs } from 'vue'

export default {
    setup () {
        // 아래의 경우 return할 때에는 ...toRefs(state),
        // const state = reactive({
        //     raduis: 5,
        // })
        const raduis = ref(5);

        // reactive안에 선언한 경우는 아래처럼 state.radius를, ref로 선언한 경우 raduis.value로 값 가져옴
        // const area = computed(() => Math.PI * state.raduis ** 2);
        const area = computed(() => Math.PI * raduis.value ** 2);
    
        const increaseRaduis = () => {
            raduis.value++;
        }

        const decreaseRaduis = () => {
            if (raduis.value > 1) {
                raduis.value--;
            }
        }
        
        return {
            // reactive로 쓰였을때에만, 
            // ...toRefs(state),
            raduis,
            area,
            increaseRaduis,
            decreaseRaduis
        }
    }
}
</script>

<style lang="scss" scoped>

</style>