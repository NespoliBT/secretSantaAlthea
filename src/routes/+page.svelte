<script>
    import { onMount } from "svelte";

    let terminal;
    let loaded = false;
    let titleName;
    let showHolidays = false;
    let mailsOpen = false;

    onMount(() => {
        const messages = terminal.querySelectorAll(".message");

        messages.forEach((message, index) => {
            setTimeout(() => {
                message.style.display = "block";
                message.scrollIntoView({
                    behavior: "smooth",
                });
                if (message.classList.contains("colors")) {
                    const colors = message.querySelectorAll(".color");
                    colors.forEach((color, index) => {
                        setTimeout(() => {
                            if (color.classList.contains("select")) {
                                color.style.color = "green";
                            }
                        }, index * 100);
                    });
                }

                if (message.classList.contains("presents")) {
                    const presents = message.querySelectorAll(".present");
                    presents.forEach((present, index) => {
                        setTimeout(() => {
                            if (present.classList.contains("select")) {
                                present.style.color = "green";
                            }
                        }, index * 100);
                    });
                }
            }, index * message.getAttribute("delay"));
        });

        const totalDelay =
            messages.length *
            messages[messages.length - 1].getAttribute("delay");

        setTimeout(() => {
            loaded = true;

            setTimeout(() => {
                titleName = "Althea";
            }, 2000);
        }, totalDelay);
    });
</script>

{#if !loaded}
    <div class="console" bind:this={terminal}>
        <div class="message info" delay="0">Avvio Secret Santa!</div>
        <div class="message ok" delay="1000">Avviato!</div>
        <div class="message info" delay="1000">Ricerca gusti...</div>
        <div class="message error" delay="800">No results found for:</div>
        <div class="message error code" delay="600">
            SELECT * FROM interests WHERE name = "Althea"
        </div>
        <br />
        <div class="message info" delay="600">
            Generazione automatica colori...
        </div>
        <div class="colors message" delay="600">
            <div class="color">Rosso</div>
            <div class="color select">Blu</div>
            <div class="color select">Verde</div>
            <div class="color select">Giallo</div>
            <div class="color">Arancione</div>
            <div class="color select">Viola</div>
            <div class="color">Rosa</div>
            <div class="color">Bianco</div>
            <div class="color">Nero</div>
            <div class="color">Marrone</div>
        </div>
        <br />
        <div class="message info" delay="800">
            Generazione automatica regalo...
        </div>
        <div class="presents message" delay="800">
            <div class="present">Letteralmente una barca</div>
            <div class="present">Un busto di mussolini</div>
            <div class="present select">La bibbia</div>
            <div class="present">Un foglio A4 di carta riciclta</div>
            <div class="present">Il mio diario di terza superiore</div>
            <div class="present">
                La moneta da 20 cent che ti ha fottuto la macchinetta due mesi
                fa
            </div>
            <div class="present select">Un cane</div>
            <div class="present">
                L'istaurazione del comunismo transfemminista galattico
            </div>
        </div>
        <br />
        <div class="message info" delay="800">
            Generazione automatica bigliettino...
        </div>
        <div class="message ok" delay="800">Bigliettino generato!</div>
        <br />
        <div class="message error" delay="750">
            Errore 403: Non hai i permessi per fare questo
        </div>
        <div class="message error" delay="700">
            Errore 401: Non sei autorizzato
        </div>
        <div class="message error" delay="700">
            Errore 400: Richiesta errata
        </div>
        <div class="message error" delay="700">Errore 409: Conflitto</div>
        <div class="message error" delay="700">
            [1.876782] Kernel panic - not syncing: UFS: Unable to Mount root fs
            on unknown-block (8,8) <br />
            [1.8777181] CPU: 8 PID: 1 COMM: Swapper/8 Not tainted 3.18.8-327. e17.x86_64
        </div>
        <div class="message error" delay="800">
            [1.878657] Hardware name: UMware, Inc. UMware Virtual Platform/440BX
            Desktop Reference Platform, BIOS 6.08 07/31/2013<br />
            [1.8795941] Call Trace:<br />
            Mount_block_root+0x2a1/8x2b0<br />
            prepare_namespace+0x13c/8x174
        </div>
        <div class="message error" delay="800">
            [ffffffff816351f1] ffffffff816351f1><br />
            [ffffffff8162ea6c] ffffffff8162ea6c<br />
            [ffffffff81a8d5fa] ffffffff81a8d5fa<br />
            [ffffffff81a8d65c] Mount_root+0x53/8x56ffffffff81a8d65c
        </div>
        <div class="message error" delay="800">
            [ffffffff81a8d268] kernel_init_freeable+8x1f8/8x217<br />
            [ffffffff81a8c9db] ? initcall_blacklist+0xb0/8xb8<br />
            [ffffffff81624e10] ? rest_init+0x88/8x80<br />
            [ffffffff81a8c9db] ? initcall_blacklist+0xb0/8xb8
        </div>
        <div class="message error" delay="800">
            dump_stack+0x19/0x1b<br />
            panic+0x1e5/0x3d0<br />
            ret_from_fork+8x58/8x98<br />
            ? rest_init+0x80/8x80
        </div>
        <div class="message info" delay="800">Avvio X Server...</div>
    </div>
{/if}

{#if loaded}
    <div class="content">
        <div class="title">
            <span
                on:mouseenter={() => (showHolidays = true)}
                on:mouseleave={() => (showHolidays = false)}>Buone Feste</span
            >
            <span>{titleName || "..."}</span>
            {#if showHolidays}
                <span class="holiday">🎄</span>
            {/if}
        </div>
        <div class="container">
            <div class="left">
                <div class="bigliettino">
                    Cara Althea, Sono lieto di scrivervi questo bigliettino per
                    augurarti un felice Natale e un nuovo anno pieno di amore,
                    gioia e pace.
                    <br /><br />
                    Spero che queste festività ti portino il calore e l'allegria
                    che meriti e che tu possa trascorrere del tempo prezioso con
                    le persone che ami.

                    <br />Vorrei ringraziarti per tutto l'affetto e il sostegno
                    che mi hai dimostrato durante l'anno. <br /><br />

                    Sei sempre stata al mio fianco nei momenti buoni e nei
                    momenti difficili, e per questo ti sono profondamente grato.
                    <br /><br />
                    Spero che questo Natale sia per te una vera benedizione e che
                    possa portare nella tua vita tanta felicità e prosperità.

                    <br /><br />Buone feste! <br />Con affetto, [Inserisci nome]
                </div>
            </div>
            <div class="right">
                <div class="mailContainer">
                    <div
                        class="mailIcon"
                        on:click={() => (mailsOpen = !mailsOpen)}
                    >
                        
                        <div class="notifications">5</div>
                    </div>
                    {#if mailsOpen}
                        <div class="mails">
                            <div class="mail">
                                <div class="mailTitle">Giallo</div>
                                <a download href="/giallo.png" class="download"
                                    >Scarica</a
                                >
                            </div>
                            <div class="mail">
                                <div class="mailTitle">Blu</div>
                                <a download href="/blu.png" class="download"
                                    >Scarica</a
                                >
                            </div>
                            <div class="mail">
                                <div class="mailTitle">Verde</div>
                                <a download href="/verde.png" class="download"
                                    >Scarica</a
                                >
                            </div>
                            <div class="mail">
                                <div class="mailTitle">Viola</div>
                                <a download href="/viola.png" class="download"
                                    >Scarica</a
                                >
                            </div>
                            <div class="mail">
                                <div class="mailTitle">Completo</div>
                                <a
                                    download
                                    href="/completo.png"
                                    class="download">Scarica</a
                                >
                            </div>
                        </div>
                    {/if}
                </div>
            </div>
        </div>
    </div>
{/if}

<style lang="scss">
    @import "../scss/main.scss";
</style>
