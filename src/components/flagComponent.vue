<template>
<div>
    <strong>Language:</strong> 
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
div{
    display: flex;
    align-items: center;
    img{
    width: 17px;
    height: 14px;
    margin-left: 3px;
    }
}
</style>