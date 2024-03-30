<script lang="ts">
	import { Collapse, Nav, NavItem, Navbar, NavbarBrand } from '@sveltestrap/sveltestrap';

	import { locale, locales } from 'svelte-i18n';

	export const setLocale = (lang: string) => () => {
		locale.set(lang);
		localStorage.setItem('locale', lang);
	};

	export const getFlagEmoji = (languageCode: string): string | null => {
		const flagMap: { [key: string]: string } = {
			en: '🇬🇧', // English flag emoji
			nl: '🇳🇱', // Dutch flag emoji
			es: '🇪🇸' // Spanish flag emoji
		};

		// Convert the language code to lowercase for case-insensitive matching
		const lowercaseCode = languageCode.toLowerCase();

		// Check if the language code is in the flagMap
		if (Object.prototype.hasOwnProperty.call(flagMap, lowercaseCode)) {
			return flagMap[lowercaseCode];
		} else {
			// Return null for unsupported language codes
			return null;
		}
	};

	let languageNames = {};

	locale.subscribe(() => {
		let newLanguageNames = new Intl.DisplayNames([$locale], { type: 'language' });

		for (let l: string of $locales) {
			languageNames[l] = newLanguageNames.of(l);
		}
	});
</script>

<Navbar expand="md">
	<NavbarBrand>
		<img src="/assets/logo-dark.svg" alt="OrangeClock" class="darkModeLogo" />
		<img src="/assets/logo.svg" alt="OrangeClock" class="lightModeLogo" />
	</NavbarBrand>
	<Collapse navbar expand="md">
		<Nav class="me-auto" navbar>
			<NavItem>WebFlasher</NavItem>
		</Nav>
	</Collapse>
</Navbar>

<!-- +layout.svelte -->
<slot />
