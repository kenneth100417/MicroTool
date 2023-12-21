<template>
     <div class="col-md-8" v-if="showAboutComponent">
        <div class="text-center mb-5 mt-5">
            <h2 class="text-primary">About</h2>
            <div class="d-flex justify-content-start" style="border-bottom: 1px solid black;">
                <p style="font-size: 24px" class="mb-5">K&K MicroTool is developed using Vue.js and Bootstrap CSS Framework. This serves as a Final project for the subject "Advance Web Application."</p>
            </div>

            <h3 class="text-primary mt-5">Group Members:</h3>
            <div class="mt-2">
                <h2>Gisalan, Kenneth L.</h2>
                <h2>Gollena, Katherine M.</h2>
                <h2>Adamos, Aljon G.</h2>
                <h2>Gerero, Charisse Erica </h2>
                <h4  style="border-top: 1px solid black; margin: 0 250px;">BSIT 4-2</h4>
            </div>
        </div>
    </div>
</template>

<script>

export default{
    props: ['showAboutComponent']
}
</script>