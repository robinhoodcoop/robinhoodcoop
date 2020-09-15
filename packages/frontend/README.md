# @robinhoodcoop/frontend

The frontend to browse the `RobinHoodCoop` DAO and its `ERC20`.

## Dependencies

  email js

  the graph

  fortmatic

  netlify

fonts.googleapis.com
css family=Monoton display=swap
@font-face {
  font-family: 'New York';
  font-weight: 700;
  src: url('fonts/NewYorkExtraLarge-Heavy.otf');

## State

# terms and conditions

in [src/sections/home/actions/Terms.md](src/sections/home/actions/Terms.md)

# emailing

in [src/routes/members/Create.svelte](src/routes/members/Create.svelte)

  const TEMPLATE_ID = 'membership_confirmation'
  const SERVICE_ID  = 'robinhoodsmtp'
  emailjs.init('user_jzjfr1GQsGlkjbK6QZpqg')


in [src/sections/home/actions/Signup.svelte](src/sections/home/actions/Signup.svelte)

  const TEMPLATE_ID = 'template_5hkdMlok'
  const SERVICE_ID  = 'robinhoodsmtp'
  emailjs.init('user_jzjfr1GQsGlkjbK6QZpqg')

# email templating

in [src/components/Mail.svelte](src/components/Mail.svelte)

    href="mailto:registration@robinhoodcoop.org?subject=[member-registration]&body=---begin%0d{user.firstname}%0d{user.lastname}%0d{user.email}%0d{user.address}%0d---end">

# addresses

in [src/lib/coop.js](src/lib/coop.js)

    ADDRESS = '0x1030e7bb1fB3a9EEE118C5cca4EBAfDAA3d350D1'

in [src/lib/share.js](src/lib/share.js)

    ADDRESS = '0xaB9382C0aD4BD6c4Efd578f54b0DA1804F766e60'

# thegraph.com

in [src/lib/graphql.js](src/lib/graphql.js)

    GRAPH_ENDPOINT = 'wss://api.thegraph.com/subgraphs/name/osarrouy/robinhoodcoop'

# fortmatic.com

in [src/lib/members.js](src/lib/members.js)

    KEY = 'pk_live_466F6781B380D059'

# validation assumptions

in [src/lib/validations.js](src/lib/validations.js)

    if (email && /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(email)) {

in [src/sections/home/actions/Signup.svelte](src/sections/home/actions/Signup.svelte)

  const phoneFormat = /^[\+]?[(]?[0-9]{3}[)]?[-\s\.]?[0-9]{3}[-\s\.]?[0-9]{4,6}$/im;

# strings

as ad hoc index, use `STRINGS.md` and find the file inside the repo accordingly. eventually, internationalization should replace this

## Development

## Testnet kovan details

### frontend

in [src/App.svelte](src/App.svelte)

kovan
network !== '42'
mainnet
network !== '1'

in [src/lib/coop.js](src/lib/coop.js)

kovan
const ADDRESS = '0xdA08FcdD705750A6738445a6E9c2D76dAE6d8576'

const provider = ethers.getDefaultProvider('kovan')

mainnet
const ADDRESS = '0x1030e7bb1fB3a9EEE118C5cca4EBAfDAA3d350D1'

const provider = ethers.getDefaultProvider('mainnet')

in [src/lib/share.js](src/lib/share.js)

kovan
const ADDRESS = '0x0dc3B1B84Ca64d06cD453C2257fa86714C024574'

const provider = ethers.getDefaultProvider('kovan')

mainnet
const ADDRESS = '0xaB9382C0aD4BD6c4Efd578f54b0DA1804F766e60'

const provider = ethers.getDefaultProvider('mainnet')

in [src/routes/admin/Error.svelte](src/routes/admin/Error.svelte)

{:else if network !== '42'}
<p>Your are connected to the wrong network. Please select the kovan network in Metamask.</p>

mainnet
{:else if network !== '1'}
<p>Your are connected to the wrong network. Please select the mainnet network in Metamask.</p>

### subgraph

in [packages/subgraph/subgraph.yaml](../subgraph/subgraph.yaml)

  name: RobinHoodCoop
    network: kovan
       address: '0xdA08FcdD705750A6738445a6E9c2D76dAE6d8576'
       startBlock: 18062977

  name: RobinHoodShare
    network: kovan
       address: '0x0dc3B1B84Ca64d06cD453C2257fa86714C024574'
       startBlock: 18062977


##### » install and link dependencies

```sh
lerna bootstrap
```

##### » compile and spawn a local dev server

```sh
npm run dev
```

##### » build

```sh
npm run build
```

## Continuous integration

This frontend is automatically [re]built and [re]deployed by [Netlify](https://www.netlify.com) each time a new commit is pushed on the `dev` branch of this repository.
