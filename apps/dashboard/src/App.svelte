<script lang="ts">
  import { onMount } from 'svelte';
  type State = 'VALID' | 'MOTION_ARTIFACT' | 'NO_TARGET' | 'SENSOR_FAULT';
  let state: State = 'VALID';
  let bpm = 68;
  let rpm = 15;
  let quality = 0.94;
  let updated = new Date();
  let history: number[] = [70, 69, 67, 66, 65, 66, 68, 68];
  let selected = 'Monitor';
  let testLog: string[] = [];
  let tick = 0;

  onMount(() => {
    const timer = window.setInterval(() => {
      tick++;
      if (state === 'VALID') {
        bpm = Math.round(67 + 4 * Math.sin(tick / 3));
        rpm = Math.round(15 + 2 * Math.sin(tick / 6));
        quality = Math.max(0.75, Math.min(0.99, 0.93 + 0.04 * Math.sin(tick / 4)));
        history = [...history.slice(-19), bpm];
      }
      updated = new Date();
    }, 2500);
    return () => window.clearInterval(timer);
  });

  function testAlert() {
    testLog = [`SIMULATED TEST · ${new Date().toLocaleTimeString()} · No external siren or phone contacted`, ...testLog].slice(0, 10);
  }
</script>

<svelte:head>
  <title>Manawa-Radar | Research Dashboard</title>
</svelte:head>

<div class="app-shell">
  <aside class="sidebar">
    <div class="brand"><div class="mark">♥</div><div><strong>Manawa-Radar</strong><small>OPEN HEALTH HARDWARE</small></div></div>
    <div class="nav-label">WORKSPACE</div>
    {#each ['Monitor', 'History', 'Alerts', 'Devices'] as item}
      <button class:active={selected === item} onclick={() => selected = item}>{item}</button>
    {/each}
    <div class="sidebar-bottom">Research prototype · v0.1<br />Not a medical device</div>
  </aside>

  <main>
    <header><div><div class="eyebrow">BEDROOM 01 / LOCAL MONITORING</div><h1>{selected}</h1></div><span class="pill">● SIMULATION MODE</span></header>
    <div class="safety">This dashboard uses synthetic data. It does not monitor a real person or detect medical emergencies.</div>

    {#if selected === 'Monitor'}
      <div class="summary">
        <div class="metric"><div class="metric-label">♥ Heart rate</div><div class="metric-value">{state === 'VALID' ? bpm : '—'} <span>bpm</span></div><div class="metric-footer">Simulated measurement</div></div>
        <div class="metric"><div class="metric-label">≋ Respiratory rate</div><div class="metric-value">{state === 'VALID' ? rpm : '—'} <span>/min</span></div><div class="metric-footer">Simulated measurement</div></div>
        <div class="metric"><div class="metric-label">◉ Signal quality</div><div class="metric-value">{state === 'VALID' ? Math.round(quality * 100) + '%' : '—'}</div><div class="metric-footer">{state.replaceAll('_', ' ')}</div></div>
      </div>
      <section class="panel"><div class="panel-heading"><h2>Heart-rate trend</h2><span>Simulated live stream</span></div><div class="chart" aria-label="Simulated heart rate history">
        {#each history as value, i}<div class="bar" title={value + ' bpm'} style:height={Math.max(8, (value - 50) * 2.8) + '%'}></div>{/each}
      </div><div class="axis"><span>Earlier</span><span>Latest</span></div></section>
      <section class="panel"><div class="panel-heading"><h2>Sensor status simulator</h2><span>Choose a synthetic state</span></div><div class="controls">
        {#each ['VALID', 'MOTION_ARTIFACT', 'NO_TARGET', 'SENSOR_FAULT'] as option}<button class:chosen={state === option} onclick={() => state = option as State}>{option.replaceAll('_', ' ')}</button>{/each}
      </div><p class="muted">When the simulated sensor loses a valid measurement, the UI displays no heart or respiratory rate rather than stale numbers.</p></section>
    {:else if selected === 'History'}
      <section class="panel"><h2>Measurement history</h2><p>Local SQLite storage and export are planned. This view currently shows only transient simulated readings.</p><p class="muted">Latest sample: {updated.toLocaleTimeString()} · {history.length} samples held in memory</p></section>
    {:else if selected === 'Alerts'}
      <section class="panel"><h2>Technical alarm test</h2><p>Test the interface and audit log without triggering external devices or notifications.</p><button class="primary" onclick={testAlert}>Run simulated alert test</button><div class="log">{#each testLog as entry}<p>{entry}</p>{:else}<p>No test events yet.</p>{/each}</div></section>
    {:else}
      <section class="panel"><h2>Device inventory</h2><p>Radar sensor · <strong>Not connected</strong></p><p>Local hub · <strong>Not connected</strong></p><p>Wireless sirens · <strong>Not connected</strong></p><p class="muted">Pairing and authenticated device discovery will be implemented after the hub protocol is validated.</p></section>
    {/if}
    <footer>Manawa-Radar · Open-source medical-device research · No clinical claims</footer>
  </main>
</div>
