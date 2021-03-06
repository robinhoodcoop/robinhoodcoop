<script>
  import { Submit }                                                         from '/components/index.js'
  import { Content, Main, Title }                                           from '/sections/admin/index.js'
  import { graphql, notify, toFormattedDecimals, toFixed, SHARE, RHC, RHS } from '/lib/index.js'
  import { onMount }                                                        from 'svelte'

  let coop      = RHC.new({ metamask: true })
  let loading   = false
  let share     = RHS.new({ metamask: true })
  let supply    = '...'
  let value     = '...'
  let timestamp = '...'
  let update

  graphql
    .subscribe({
      query: SHARE,
    })
    .subscribe(async result => {
      const date = new Date(result.data.share.timestamp * 1000)
      timestamp  = date.getDate() + '.' + (date.getMonth() + 1) + '.' + date.getFullYear()
    })

  const fetchValueAndSupply = async () => {
    value = toFormattedDecimals(await coop.value())
    supply = toFormattedDecimals(await share.totalSupply())
  }

  const updateValue = async () => {
    loading = true

    try {
      const tx = await coop.updateValue(toFixed(update))
      notify.default("Value being updated through tx <a href=https://etherscan.io/tx/" + tx.hash + " target='_blank' >" + tx.hash + "</a>")
      await tx.wait()
      notify.success('Value updated')
      update = null
      await fetchValueAndSupply()
    } catch (e) {
      notify.error(e.message)
    }

    loading = false
  }

  onMount(() => {
    fetchValueAndSupply()
  })
</script>

<style type="text/scss">
  :global(.shares) {
    display: flex;
    flex-direction: column;
    min-height: calc(100vh - #{2 * $spacing});
    align-items: flex-start;
    justify-content: center;

    table {
      border-collapse: separate;
      border-spacing: #{2 * $spacing} $spacing;
      margin-top: #{$spacing};
      // margin-bottom: -#{$spacing};
      margin-left: -#{2 * $spacing};
    }
  }
</style>

<Main>
  <Title>
    <h1>Shares</h1>
  </Title>
  <Content class="shares">
    <table>
      <tr>
        <td class="strong">supply</td>
        <td>{supply} shares</td>
      </tr>
      <tr>
        <td class="strong">value</td>
        <td>
          <span>{value} EUR / share</span>
        </td>
      </tr>
    </table>
    <p class="info">last updated on {timestamp}</p>
    <form class="flex space-top" on:submit|preventDefault={updateValue}>
      <input type="number" min="0" step="0.01" bind:value={update} placeholder={value} class="space-right" />
      <Submit type="small" disabled={loading} value="update value" />
    </form>
  </Content>
</Main>
