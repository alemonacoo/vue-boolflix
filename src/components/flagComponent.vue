<template>
<div>
    <img :src="getFlag(language)" :alt="language">
</div>
</template>

<script>
export default {
    name: 'FlagComponent',
    props:{
        language: String,
    }, methods:{
        getFlag(country){
            switch(country){
                case 'en':{
                    country = 'gb';
                    break;
                }
                case 'ja':{
                    country = 'jp'
                    break;
                }
            }
            return `https://flagicons.lipis.dev/flags/1x1/${country}.svg`
        }
    }

}
</script>

<style lang="scss" scoped>
img{
    width: 20px;
}

</style>