<script lang="ts">
	//	import { PUBLIC_BASE_URL } from '$lib/config';

	import {
		Container,
		Col,
		Card,
		CardHeader,
		CardTitle,
		CardBody,
		Button,
		Row
	} from '@sveltestrap/sveltestrap';
	// import Settings from './Settings.svelte';
	// import Status from './Status.svelte';
	// import Control from './Control.svelte';
</script>

<svelte:head>
	<title>OrangeBTClock</title>
	<script
		type="module"
		src="https://unpkg.com/esp-web-tools@10/dist/web/install-button.js?module"
	></script>
</svelte:head>

<Container>
	<Row>
		<Col>
			<Card>
				<CardHeader>
					<CardTitle>Wemos S2/S3 mini</CardTitle>
				</CardHeader>
				<CardBody>
					<esp-web-install-button manifest="/manifests/epd2_13.json">
						<span slot="activate"><Button color="primary">2.13 inch</Button></span>
					</esp-web-install-button>
					<esp-web-install-button manifest="/manifests/epd2_9.json">
						<span slot="activate"><Button color="secondary">2.9 inch</Button></span>
					</esp-web-install-button>
				</CardBody>
			</Card>
		</Col>
		<Col>
			<Card>
				<CardHeader>
					<CardTitle>OrangeClock PCB</CardTitle>
				</CardHeader>
				<CardBody>
					<esp-web-install-button manifest="/manifests/oc_pcb.json">
						<span slot="activate"><Button color="secondary">2.9 inch</Button></span>
					</esp-web-install-button>
				</CardBody>
			</Card>
		</Col>
	</Row>
	<Row>
		<Col>
			<h1>How it works</h1>
			<p>
				ESP Web Tools works by using Web Serial and a manifest which describes the firmware. ESP Web
				Tools detects the chipset of the connected ESP device and automatically selects the right
				firmware variant from the manifest.
			</p>
			<p>
				Web Serial is available in Google Chrome and Microsoft Edge browsers. Android support should
				be possible but has not been implemented yet.
			</p>
		</Col>
	</Row>
</Container>
