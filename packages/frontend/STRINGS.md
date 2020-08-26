in `src/routes/admin/admins/Create.svelte`

  error = 'this address already belongs to an existing admin'
  error = 'invalid ethereum address'
  notification = Admin being added through tx ' + tx.hash)
  notification = Admin added. You will be redirected soon ...

in `src/routes/admin/admins/List.svelte`

  notification = Admin being revoked through tx ' + tx.hash)
  notification = Admin revoked
  button = add an admin
  a = revoke »
  this is you ...

in `src/routes/admin/members/edit/Burn.svelte`

  notification = Shares being burnt through tx ' + tx.hash)
  notification = Shares burnt. You will be redirected soon ...
  notification = Shares being burnt through tx ' + tx.hash)
  notification = Shares burnt
  WARNING.
  This amount will be burnt and therefore
  substracted
  to the current member's balance.


in `src/routes/admin/members/edit/Mint.svelte`

  notification = Shares being minted through tx ' + tx.hash)
  notification = Shares minted
  WARNING.
  This amount will be minted and therefore
  added
  to the current member's balance.


in `src/routes/admin/members/Create.svelte`

  errors.address = 'this address already belongs to an existing member'
  errors.address = 'invalid ethereum address'
  errors.email = 'invalid email address'
  errors.shares = 'invalid amount of shares'
  notification = Member being added through tx ' + tx.hash
  notification = Member added. You will be redirected soon ...

in `src/routes/admin/members/Edit.svelte`

  link = « go back
  error = Unknown member {address}

in `src/routes/admin/members/List.svelte`

  Members
  button = add a member
  Address
  Shares
  link = edit »

in `src/routes/admin/shares/Shares.svelte`

  notification = Value being updated through tx ' + tx.hash
  notification = Value updated
  Shares
  shares
  EUR / share
  last updated on

in `src/routes/admin/Error.svelte`

  Your are connected to the wrong network. Please select the mainnet network in Metamask.
  Your are not identified as a RobinHoodCoop admin. Please pick up a different account in Metamask.

in `src/routes/NotFound.svelte`

  404
  not found

in `src/sections/admin/Nav.svelte`

  link = members
  link = admins
  link = shares


in `src/sections/home/actions/Dispatch.svelte`

  message = "Your account needs to be activated by an admin.\nRHcoop will send you an email as soon as your account is ready for log in.\nKeep an eye on your inbox [and spam folder too]."
  button = login
  button = signup

in `src/sections/home/actions/Login.svelte`

  message = 'Check your inbox [including your spam folder].'
  message = 'Your account needs to be activated by an admin. RHcoop will send you an email as soon as your account is ready for log in. Keep an eye on your inbox [and spam folder too].'
  checking if a member is already logged in ...


in `src/sections/home/actions/Signup.svelte`

  message += '\nplease provide a valid email'
  message += '\nplease provide a valid phone number'
  message += '\nplease provide your firstname'
  message += '\nplease provide your lastname'
  message += '\nplease agree with the terms and conditions'
  message = 'You are already signed up with this address. Go back and login.'
  Your membership request has been submitted to review by an admin.
  We will come back to you soon.
  Your membership request will be reviewed by an admin. Please:
  1. use your real name
  1. use the same email you are identified with if you already are a RobinHood member
  Once you click on 'signup' a Fortmatic window will pop up. This Formatic account will identify you on this platform.
  me@mail.com
  phone number
  1 Rue des Dames, 75001 Paris, France
  terms and conditions.

in `src/sections/home/Data.svelte`

  shares
  EUR per share
  € total
  values as of
  850
  members
  total coop shares
  EUR per share
  last updated on
  850
  members
  total coop shares
  EUR per share
  last updated on

in `src/sections/home/Nav.svelte`

  link = go back
  link = logout

in `src/sections/home/Titel.svelte`

  Your portfolio
  Robin Hood Coop
