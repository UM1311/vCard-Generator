<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    
    export let values = {
    name: "",
    organisation: "",
    jobTitle: "",
    phone: "",
    address: "",
    email: "",
    photoURL: "https://picsum.photos/150/200",
    logoURL: "https://icongr.am/material/home.svg?size=40&color=3d9afd",
    backgroundURL:"https://source.unsplash.com/random/1200x800"
    };

    let disabled = true;
    let firstInput;
    let active = {
    name: false,
    organisation: false,
    jobTitle: false,
    phone: false,
    address: false,
    email: false,
    photoURL: false,
    logoURL: false,
    backgroundURL: false
    };

    const inputsData = {
    name: {
        label: "Name",
        type: "text",
        placeholder: "Your contact name"
    },

    organisation: {
        label: "Organisation",
        type: "text",
        placeholder: "Name of your organisation"
    },

    jobTitle: {
        label: "Job Title",
        type: "text",
        placeholder: "Your job title"
    },

    phone: {
        label: "Phone number",
        type: "text",
        placeholder: "Your phone number"
    },

    address: {
        label: "Address",
        type: "text",
        placeholder: "Professional address"
    },
    
    email: {
        label: "E-Mail",
        type: "email",
        placeholder: "Professional E-Mail address"
    },
    
    photoURL: {
        label: "Photo",
        type: "text",
        placeholder: "URL of personal portrait"
    },
    
    logoURL: {
        label: "Company logo",
        type: "text",
        placeholder: "URL of your company's logo"
    },
    
    backgroundURL: {
        label: "Background image",
        type: "text",
        placeholder: "URL of card's background (leave blank for none)"
    }
    };

//     function resizeImage(url, width, height) {
//     try {
//         const regex = /(width=\d+&height=\d+)/;
//         const newSize = `width=${width}&height=${height}`;
//         return url.match(regex) ? url.replace(regex, newSize) : url + (url.includes('?') ? '&' : '?') + newSize;
//     } catch (error) {
//         console.error("Error resizing image:", error);
//         return url; // Return the original URL if there's an error
//     }
// }
//     values.photoURL = resizeImage(values.photoURL, 300);
//     values.logoURL = resizeImage(values.logoURL, 60);
//     values.backgroundURL = resizeImage(values.backgroundURL, 1000, 500);


    // If the reset button is clicked disable it
    function resetClicked() {
    disabled = true;
    values = {
        name: "",
        organisation: "",
        jobTitle: "",
        phone: "",
        address: "",
        email: "",
        photoURL: "",
        logoURL: "",
        backgroundURL: ""
    };
    firstInput.focus();
    }

    // If shift key is pressed without any input
    function keyPressed(event) {
    event.key === "Shift" ? "" : (disabled = false);
    }
</script>

<style>
    label {
    display: flex;
    align-items: baseline;
    margin: 0.5rem;
    font-weight: bold;
    }
    input {
    width: 70%;
    margin: 0 0.5rem;
    border-radius: 5px;
    }
    article {
    display: flex;
    justify-content: space-evenly;
    }
    button {
    margin: 0.5rem 0;
    cursor: pointer;
    border-radius: 5px;
    }
    .labelText {
    text-align: end;
    width: 30%;
    }
    .active {
    border-color: hsl(211, 63%, 35%);
    box-shadow: 0 1px 3px hsla(211, 63%, 35%, 0.4);
    }
</style>

<form>
    <!-- Name -->
    <label>
    <div class="labelText">{inputsData.name.label}</div>
    <input
        type="text"
        placeholder={inputsData.name.placeholder}
        class:active={active.name}
        on:focus={() => {
        active.name = true;
        }}
        on:blur={() => {
        active.name = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.name}
        bind:this={firstInput} />
    </label>
    <!-- Organisation -->
    <label>
    <div class="labelText">{inputsData.organisation.label}</div>
    <input
        type="text"
        placeholder={inputsData.organisation.placeholder}
        class:active={active.organisation}
        on:focus={() => {
        active.organisation = true;
        }}
        on:blur={() => {
        active.organisation = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.organisation} />
    </label>
    <!-- Job Titl -->
    <label>
        <div class="labelText">{inputsData.jobTitle.label}</div>
        <input
        type="text"
        placeholder={inputsData.jobTitle.placeholder}
        class:active={active.jobTitle}
        on:focus={() => {
    active.jobTitle = true;
        }}
        on:blur={() => {
    active.jobTitle = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.jobTitle} />
    </label>
    <!-- Phone  -->
    <label>
        <div class="labelText">{inputsData.phone.label}</div>
        <input
        type="text"
        placeholder={inputsData.phone.placeholder}
        class:active={active.phone}
        on:focus={() => {
        active.phone = true;
        }}
        on:blur={() => {
        active.phone = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.phone} />
    </label>
    <!-- Address  -->
    <label>
    <div class="labelText">{inputsData.address.label}</div>
    <input
        type="text"
        placeholder={inputsData.address.placeholder}
        class:active={active.address}
        on:focus={() => {
        active.address = true;
        }}
        on:blur={() => {
        active.address = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.address} />
    </label>
    <!-- E-mail  -->
    <label>
    <div class="labelText">{inputsData.email.label}</div>
    <input
        type="email"
        placeholder={inputsData.email.placeholder}
        class:active={active.email}
        on:focus={() => {
        active.email = true;
        }}
        on:blur={() => {
        active.email = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.email} />
    </label>
    <!-- Photo URL -->
    <label>
    <div class="labelText">{inputsData.photoURL.label}</div>
    <input
        type="text"
        placeholder={inputsData.photoURL.placeholder}
        class:active={active.photoURL}
        on:focus={() => {
        active.photoURL = true;
        }}
        on:blur={() => {
        active.photoURL = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.photoURL} />
    </label>
    <!-- logoURL -->
    <label>
    <div class="labelText">{inputsData.logoURL.label}</div>
    <input
        type="text"
        placeholder={inputsData.logoURL.placeholder}
        class:active={active.logoURL}
        on:focus={() => {
        active.logoURL = true;
        }}
        on:blur={() => {
        active.logoURL = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.logoURL} />
    </label>
    <!-- backgroundURL -->
    <label>
    <div class="labelText">{inputsData.backgroundURL.label}</div>
    <input
        type="text"
        placeholder={inputsData.backgroundURL.placeholder}
        class:active={active.backgroundURL}
        on:focus={() => {
        active.backgroundURL = true;
        }}
        on:blur={() => {
        active.backgroundURL = false;
        }}
        on:keydown={keyPressed}
        bind:value={values.backgroundURL} />
    </label>

    <article>
    <button {disabled} on:click|preventDefault={resetClicked}>Reset</button>
    <button
        on:click|preventDefault={() => {
        dispatch('createQRCode', true);
        }}>
        Create QR Code
    </button>
    </article>
</form>