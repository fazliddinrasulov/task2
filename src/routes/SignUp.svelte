<script>

   import ResultV1 from "./ResultV1.svelte";
   import ResultV2 from "./ResultV2.svelte";
   
    let currentStep = 1;
    let carBrand;
    let zipCode;
    let firstName;
    let lastName;
    let carModel;
    let firstRegistration;
    let random = Math.floor(Math.random()*2)
    
    function increment() {
        progress = 100;
    }

    function validateStep1 () {
    if (!carBrand || !zipCode) {
      alert("Please fill out all required fields.");
      return false;
    }

    if (carBrand !== "Audi" && carBrand !== "BMW" && carBrand !== "Nissan") {
      alert("Invalid car brand. Please choose from Audi, BMW, or Nissan.");
      return false;
    }

    if (zipCode < 65000 || zipCode > 68000) {
      alert("Unfortunately, this postal code is not serviced.");
      return false;
    }

    return true;
  }

  function validateStep2() {
    if (!firstName || !lastName || !carModel || !firstRegistration) {
      alert("Please fill out all required fields.");
      return false;
    }

    return true;
  }

  function handleBack() {
    if (currentStep > 1) {
      currentStep--;
    }
  }

  function handleNext() {
    if (currentStep === 1) {
      if (!validateStep1()) return 
    } else if (currentStep === 2) {
      if (!validateStep2()) return;
    }

    currentStep++;
  }
</script>

<div>
  {#if currentStep === 1}
    <form>
      <label for="carBrand">Car Brand:</label>
      <input type="text" bind:value={carBrand} id="carBrand" required />

      <label for="zipCode">Zip Code:</label>
      <input type="text" bind:value={zipCode} id="zipCode" required />

      <button on:click={handleBack}>Back</button>
      <button on:click={handleNext}>Next</button>
    </form>
  {:else if currentStep === 2}
    <form>
      <label for="firstName">First Name:</label>
      <input type="text" bind:value={firstName} id="firstName" required />

      <label for="lastName">Last Name:</label>
      <input type="text" bind:value={lastName} id="lastName" required />

      <label for="carModel">Car Model:</label>
      <input type="text" bind:value={carModel} id="carModel" required />

      <label for="firstRegistration">First Registration:</label>
      <input type="text" bind:value={firstRegistration} id="firstRegistration" required />

      <button on:click={handleBack}>Back</button>
      <button on:click={handleNext}>Next</button>
    </form>


  {:else if random ===0}
        <ResultV1 carBrand={carBrand}
                  zipCode ={zipCode};
                  firstName ={firstName};
                  lastName = {lastName};
                  carModel = {carModel};
                  firstRegistration={firstRegistration};/>
   {:else if random ===1}
        <ResultV2 carBrand={carBrand}
                  zipCode ={zipCode};
                  firstName ={firstName};
                  lastName = {lastName};
                  carModel = {carModel};
                  firstRegistration={firstRegistration};/>
  {/if}
</div>

   

