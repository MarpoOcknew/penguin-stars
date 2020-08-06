<template>
    <GridLayout class="ratings-wrap" padding="0" :horizontalAlignment="position" verticalAlignment="top" :maxWidth="(colWidth*5)">
        <GridLayout :columns="colWidth+','+colWidth+','+colWidth+','+colWidth+','+colWidth" class="stars-inactive" horizontalAlignment="left" verticalAlignment="top" v-if="$isAndroid">
            <Label col="0" text.decode="&#xf005;" class="fas" color="rgbs(0,0,0,0.5)" :fontSize="size" padding="0"></Label>
            <Label col="1" text.decode="&#xf005;" class="fas" color="rgbs(0,0,0,0.5)" :fontSize="size" padding="0"></Label>
            <Label col="2" text.decode="&#xf005;" class="fas" color="rgbs(0,0,0,0.5)" :fontSize="size" padding="0"></Label>
            <Label col="3" text.decode="&#xf005;" class="fas" color="rgbs(0,0,0,0.5)" :fontSize="size" padding="0"></Label>
            <Label col="4" text.decode="&#xf005;" class="fas" color="rgbs(0,0,0,0.5)" :fontSize="size" padding="0"></Label>
        </GridLayout>

        <GridLayout :columns="colWidth+','+colWidth+','+colWidth+','+colWidth+','+colWidth" class="stars-active" horizontalAlignment="left" verticalAlignment="top" :width="(rating/5)*(colWidth*5)" v-if="$isAndroid">
            <Label col="0" text.decode="&#xf005;" class="fas" :color="starColor" :fontSize="size" padding="0"></Label>
            <Label col="1" text.decode="&#xf005;" class="fas" :color="starColor" :fontSize="size" padding="0"></Label>
            <Label col="2" text.decode="&#xf005;" class="fas" :color="starColor" :fontSize="size" padding="0"></Label>
            <Label col="3" text.decode="&#xf005;" class="fas" :color="starColor" :fontSize="size" padding="0"></Label>
            <Label col="4" text.decode="&#xf005;" class="fas" :color="starColor" :fontSize="size" padding="0"></Label>
        </GridLayout>

        <GridLayout columns="auto,auto" class="stars-inactive" horizontalAlignment="left" verticalAlignment="top" v-if="$isIOS">
            <Label col="0" :text="rating" :color="textColor" :fontSize="size" padding="0" marginRight="5"></Label>
            <Label col="1" text.decode="&#xf005;" class="fas" :color="starColor" :fontSize="size" padding="0"></Label>
        </GridLayout>
    </GridLayout>
</template>

<script>
    export default {
        name: 'StarRating',
        props: {
            rating: {
                type: [String, Number],
                default: 3,
                validation: s => !isNaN(s)
            },
            size: {
                type: [String, Number],
                default: 15,
                validation: s => !isNaN(s)
            },
            colWidth: {
                type: [String, Number],
                default: 20,
                validation: s => !isNaN(s)
            },
            textColor: {
                type: [String],
                default: 'white',
            },
            starColor: {
                type: [String],
                default: '#F3594A',
            },
            position: {
                type: [String],
                default: 'right',
            },
        },
        computed: {
            width () {
                return 'width: ' + (this.rating/5)*100 + ';' ;
            }
        },
    };
</script>

<style scoped>
    .ratings-wrap {
        height: 30;
    }

    .stars-active {
        overflow: hidden;
    }

    .stars-inactive {
        overflow: hidden;
    }

    .fas {
        padding: 0;
    }
</style