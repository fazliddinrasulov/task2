<script>
    export let carBrand
    export let zipCode
    export let firstName
    export let lastName
    export let carModel
    export let firstRegistration
</script>


<div class="result__2">
    <div>
        <h2>Fullname:</h2>
        <p>First Name: {firstName}</p>
        <p>Last Name: {lastName}</p>
    </div>
    <div>
        <h2>Entered Data:</h2>
        <p>Car Brand: {carBrand}</p>
        <p>Zip Code: {zipCode}</p>
        <p>Car Model: {carModel}</p>
        <p>First Registration: {firstRegistration}</p>
    </div>
    
</div>

<style>
    .result__2{
        display: flex;
        width: 30%;
        justify-content: space-between;
    }
</style>