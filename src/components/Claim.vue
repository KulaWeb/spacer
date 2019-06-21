<template>
<div class="claim_wrapper">
    <h1 class="claim">Spacer</h1>
    <p class="claim_p">Lets start your awsome joureney with my aplication</p>
    <p class="claim_p">Search anything you want</p>
</div>
</template>

<script>
    export default {
      name: 'Claim',
    };
</script>

<style lang="scss" scoped>

    .claim_wrapper {
        text-align: center;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    .claim {
        font-size: 45px;
        margin: 0;
        text-transform: uppercase;

        @media (min-width: 768px) {
            font-size: 80px;
        }
    }
    .claim_p {
        font-size: 13px;
        margin:  20px 0 0 0;
        @media (min-width: 768px) {
            font-size: 18px;
            letter-spacing: 1px;
            font-weight: 300;
        }
    }

</style>
