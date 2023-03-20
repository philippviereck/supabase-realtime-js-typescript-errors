<script lang="ts">
	import { browser } from '$app/environment'
	import { onDestroy } from 'svelte'
	import { supabaseClient } from '$lib/supabaseClient'
	import SupabaseProvider from '$lib/y-supabase-custom'
	import * as Y from 'yjs'

	const ydoc = new Y.Doc()

	const provider = browser
		? new SupabaseProvider(ydoc, supabaseClient, {
				channel: 'demo',
				id: 'demo1',
				tableName: 'notes',
				columnName: 'ydoc'
		  })
		: null

	onDestroy(() => {
		provider?.destroy()
	})
</script>
