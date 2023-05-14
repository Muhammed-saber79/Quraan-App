<template>
    <div class="container">
        <div class="row">

            <h2>Quraan App</h2>
            <hr>
            <div v-for="item in suar.reciters" :key="item.id" class="card col-4 my-2">
                <div class="card-body">
                    <h4 class="card-title">{{ item.name }}</h4>
                    <hr>
                    <a :href="item.moshaf[0].server + '/001.mp3'" target="_blank">surah</a>
                    <audio src=""></audio>
                </div>
            </div>

        </div>
    </div>
</template>

<script>
    export default{
        data() {
            return {
                suar: []
            }
        },
        methods: {
            test(){
                console.log(this.suar.reciters[0].moshaf[0].server);
            }
        },
        async created() {
            try{
                let response = await fetch("https://www.mp3quran.net/api/v3/reciters?language=ar");
                let data = await response.json();
                this.suar = data;

                console.log(data);
            }catch(error){
                console.log("Error: " . error);
            }
        },
    }
</script>