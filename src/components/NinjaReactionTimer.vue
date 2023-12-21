<template>
    <div class="col-md-8" v-if="showNinjaReactionTimerComponent">
        <div class="text-center mb-5 mt-5">
            <h1 class="text-success">Coming Soon!</h1>
        </div>   
    </div>
</template>

<script>
export default{
    props:['showNinjaReactionTimerComponent']
}
</script>