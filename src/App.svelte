<script lang="ts">
  let formData = {
    amount: '',
    accountType: '',
    creditObligation: '',
    firstName: '',
    otherName: '',
    surname: '',
    dateOfBirth: '',
    gender: '',
    driversLicenceNumber: '',
    unitNumber: '',
    streetNumber: '',
    streetName: '',
    streetType: '',
    suburbTown: '',
    state: '',
    postcode: ''
  };

  async function handleSubmit() {
    try {
      const url = "https://hook.eu2.make.com/24tcxwwwia5aflabtbpu0rs16bgaz9af";
      const response = await fetch(url, {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(formData),
      });

      if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
      }

      const data = await response.json();
      console.log("Form submitted successfully:", data);
      alert("Form submitted successfully!");
    } catch (error) {
      console.error("There was a problem with the form submission:", error);
      alert("There was an error submitting the form. Please try again.");
    }
  }
</script>

<main class="container mx-auto p-6 max-w-2xl">
  <h1 class="text-3xl font-bold mb-6 text-center">Credit File</h1>
  <div role="tablist" class="tabs tabs-boxed">
    <a role="tab" class="tab tab-active">Illion</a>
    <a role="tab" class="tab ">Equifax</a>

  </div>
  <form on:submit|preventDefault={handleSubmit} class="space-y-6">
    <div class="flex flex-col space-y-2">
      <label for="amount" class="font-medium">Amount:</label>
      <input type="number" id="amount" bind:value={formData.amount} required class="border rounded-md p-2" />
    </div>

    <div class="flex flex-col space-y-2">
      <label for="accountType" class="font-medium">Account Type:</label>
      <select id="accountType" bind:value={formData.accountType} required class="select select-bordered w-full" placeholder="Select an account type">
        <option value="">Select Account Type</option>
        <option value="016">Real Estate Mortgage</option>
        <option value="020">Telecommunications</option>
        <option value="021">Terms</option>
        <option value="011">Loan Contract</option>
        <option value="024">Utilities</option>
        <option value="013">Overdraft</option>
        <option value="017">Rental or Equipment Hire</option>
        <option value="027">Other</option>
        <option value="022">Trade Finance</option>
        <option value="008">Hire Purchase</option>
        <option value="003">Cash on Delivery</option>
        <option value="018">Revolving Credit</option>
        <option value="001">Bill Of Sale</option>
        <option value="009">Lease Agreement</option>
        <option value="004">Dealership</option>
        <option value="002">Bridging Finance</option>
        <option value="005">Debit Card</option>
        <option value="006">Director's Access</option>
        <option value="007">Factored Account</option>
        <option value="031">Hire Purchase and Revolving Credit</option>
        <option value="010">Lending Proposal</option>
        <option value="012">Mortgage Insurance</option>
        <option value="026">Other Mortgage</option>
        <option value="014">Premium Finance</option>
        <option value="015">Professional Inquiry</option>
        <option value="019">Search Request</option>
        <option value="023">Transactional or Cheque Account</option>
        <option value="025">Wholesale Finance</option>
        <option value="N/A">Work Cover</option>
      </select>
    </div>

    <div class="flex flex-col space-y-2">
      <label for="creditObligation" class="font-medium">Credit Obligation:</label>
      <select id="creditObligation" bind:value={formData.creditObligation} required class="select select-bordered w-full">
        <option value="">Select Credit Obligation</option>
        <option value="002">Director</option>
        <option value="003">Guarantor</option>
        <option value="004">Joint</option>
        <option value="005">Principal</option>
        <option value="006">Proprietor</option>
      </select>
    </div>

    <fieldset class="border rounded-md p-4 space-y-4">
      <legend class="font-bold px-2">Personal Information</legend>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div class="flex flex-col space-y-2">
          <label for="firstName" class="font-medium">First Name:</label>
          <input type="text" id="firstName" bind:value={formData.firstName} required class="border rounded-md p-2" />
        </div>

        <div class="flex flex-col space-y-2">
          <label for="otherName" class="font-medium">Other Name:</label>
          <input type="text" id="otherName" bind:value={formData.otherName} class="border rounded-md p-2" />
        </div>

        <div class="flex flex-col space-y-2">
          <label for="surname" class="font-medium">Surname:</label>
          <input type="text" id="surname" bind:value={formData.surname} required class="border rounded-md p-2" />
        </div>

        <div class="flex flex-col space-y-2">
          <label for="dateOfBirth" class="font-medium">Date of Birth:</label>
          <input type="date" id="dateOfBirth" bind:value={formData.dateOfBirth} required class="border rounded-md p-2" />
        </div>

        <div class="flex flex-col space-y-2">
          <label for="gender" class="font-medium">Gender:</label>
          <select id="gender" bind:value={formData.gender} required class="border rounded-md p-2">
            <option value="">Select gender</option>
            <option value="M">Male</option>
            <option value="F">Female</option>
            <option value="U">Unknown</option>
          </select>
        </div>

        <div class="flex flex-col space-y-2">
          <label for="driversLicenceNumber" class="font-medium">Driver's Licence Number:</label>
          <input type="text" id="driversLicenceNumber" bind:value={formData.driversLicenceNumber} class="border rounded-md p-2" />
        </div>
      </div>

      <fieldset class="border rounded-md p-4 space-y-4">
        <legend class="font-bold px-2">Address</legend>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div class="flex flex-col space-y-2">
            <label for="unitNumber" class="font-medium">Unit Number:</label>
            <input type="text" id="unitNumber" bind:value={formData.unitNumber} class="border rounded-md p-2" />
          </div>

          <div class="flex flex-col space-y-2">
            <label for="streetNumber" class="font-medium">Street Number:</label>
            <input type="text" id="streetNumber" bind:value={formData.streetNumber} required class="border rounded-md p-2" />
          </div>

          <div class="flex flex-col space-y-2">
            <label for="streetName" class="font-medium">Street Name:</label>
            <input type="text" id="streetName" bind:value={formData.streetName} required class="border rounded-md p-2" />
          </div>

          <div class="flex flex-col space-y-2">
            <label for="streetType" class="font-medium">Street Type:</label>
            <input type="text" id="streetType" bind:value={formData.streetType} required class="border rounded-md p-2" />
          </div>

          <div class="flex flex-col space-y-2">
            <label for="suburbTown" class="font-medium">Suburb/Town:</label>
            <input type="text" id="suburbTown" bind:value={formData.suburbTown} required class="border rounded-md p-2" />
          </div>

          <div class="flex flex-col space-y-2">
            <label for="state" class="font-medium">State:</label>
            <input type="text" id="state" bind:value={formData.state} required class="border rounded-md p-2" />
          </div>

          <div class="flex flex-col space-y-2">
            <label for="postcode" class="font-medium">Postcode:</label>
            <input type="text" id="postcode" bind:value={formData.postcode} required class="border rounded-md p-2" />
          </div>
        </div>
      </fieldset>
    </fieldset>

    <button type="submit" class="w-full bg-blue-500 text-white font-bold py-2 px-4 rounded-md hover:bg-blue-600 transition duration-300">Submit</button>
  </form>
</main>

