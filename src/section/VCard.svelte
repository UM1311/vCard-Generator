<script>
    import Flex from "../Layout/Flex.svelte";
  
    export let QRCode = false;
    export let values = {
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
    $: qrString = `BEGIN:VCARD
VERSION:4.0
N:${values.name};${values.name};;;
FN:${values.name}
ORG:${values.organisation}
TITLE:${values.jobTitle}
TEL;TYPE=work;VALUE=uri:${values.phone}
ADR;TYPE=WORK;PREF=1;LABEL="${values.address}":;;${values.address}
EMAIL;TYPE=WORK:${values.email}
REV:20080424T195243Z
x-qq:21588891
END:VCARD`;
  </script>
  
  <style>
    
 
    section {
  max-width: 500px; /* Adjust the maximum width as needed */
  width: 100%;
  height: auto; /* Allow height to adjust based on content */
  padding: 1.5rem; /* Adjust padding for content spacing */
  margin: 2rem auto; /* Center the card with some top margin */
  border-radius: 10px;
  position: relative;
  font-size: 1rem;
  color: white;
  box-shadow: 0 1px 3px hsla(0, 0%, 0%, 0.12), 0 1px 2px hsla(0, 0%, 0%, 0.24);
  background: linear-gradient(
    to bottom right,
    rgba(16, 24, 26, 0.8),
    rgba(33, 87, 145, 0.8)
  ), var(--bg-image);
  background-size: cover;
}


  h1 {
    color: rgb(61, 154, 253);
    text-transform: uppercase;
    font-size: 1rem; /* Adjust the font size as needed */
    margin-bottom: 0.5rem;
  }

  h2 {
    color: rgb(61, 154, 253);
    font-size: 1rem; /* Adjust the font size as needed */
    margin-bottom: 0.3rem;
  }
  
  .logo img {
  width: 20px; /* Adjust the width of the logo as needed based on the smaller card */
  height: 20px; /* Adjust the height of the logo as needed based on the smaller card */
  vertical-align: middle; /* Align the image vertically in the middle */
  margin-right: 0.5rem; /* Increase the right margin for better spacing */
  margin-bottom: 0.2rem;
}

  #photo {
    border-radius: 50%;
    border: 2px solid rgb(61, 154, 253);
    width: 80px; /* Adjust the width of the photo as needed */
    height: 80px; /* Adjust the height of the photo as needed */
    margin-bottom: 0.5rem;
  }

  #qrcode {
    margin-top: 0.5rem;
  }
</style>

  
  <section style="--bg-image: {'url(' + values.backgroundURL + ')'}">
  
    <Flex justify={'space-between'} align={'start'}>
      <!-- Flexing row wise entity(Portrait, Phone, Address and E-Mail Symbols) -->
      <Flex direction={'column'}>
        {#if values.photoURL}
          <picture>
            <img id="photo" src={values.photoURL} alt="avatar" />
          </picture>
        {/if}

        {#if values.name}
          <h1>{values.name}</h1>
        {/if}

        {#if values.jobTitle}
          <h3>{values.jobTitle}</h3>
        {/if}

        {#if values.phone}
          <Flex>
            <picture class="logo">
              <img
                src="https://icongr.am/entypo/old-phone.svg?size=20&color=ffffff"
                alt="phone" />
            </picture>
            <span>{values.phone}</span>
          </Flex>
        {/if}

        {#if values.address}
          <Flex>
            <picture class="logo">
              <img
                src="https://icongr.am/entypo/address.svg?size=20&color=ffffff"
                alt="address" />
            </picture>
            <span>{values.address}</span>
          </Flex>
        {/if}

        {#if values.email}
          <Flex>
            <picture class="logo">
              <img
                src="https://icongr.am/entypo/email.svg?size=20&color=ffffff"
                alt="email" />
            </picture>
            <span>{values.email}</span>
          </Flex>
        {/if}

      </Flex>
      <!-- Flexing column wise entity (Company logo,Organization Name,QRCode) -->
      <Flex direction={'column'} align={'end'}>
        <Flex align="center">
          {#if values.logoURL}
            <picture class="logo">
              <img src={values.logoURL} alt="logo" />
            </picture>
          {/if}
          {#if values.organisation}
            <h2>{values.organisation}</h2>
          {/if}
        </Flex>
        {#if QRCode}
        <picture id="qrcode">
          <img
            src={`https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=${encodeURI(qrString)}`}
            alt="qrcode" />
        </picture>
      {/if}
      </Flex>
    </Flex>
  </section>