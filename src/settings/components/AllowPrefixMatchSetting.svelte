<script lang="ts">
  import type { Writable } from "svelte/store";

  import type { Granularity, PeriodicConfig } from "src/types";
  import { displayConfigs } from "src/commands";

  import SettingItem from "./SettingItem.svelte";
  import Toggle from "./Toggle.svelte";

  export let config: Writable<PeriodicConfig>;
  export let granularity: Granularity;
</script>

<SettingItem
  name="Allow prefix matching"
  description={`Match ${displayConfigs[granularity].periodicity} notes that start with the format (e.g., "2026-W07, 09.02 - 15.02.md" matches "gggg-[W]ww")`}
  type="toggle"
  isHeading={false}
>
  <Toggle
    slot="control"
    isEnabled={$config.allowPrefixMatch ?? false}
    onChange={(val) => {
      $config.allowPrefixMatch = val;
    }}
  />
</SettingItem>
