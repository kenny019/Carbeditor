<script>
    import {
        Header,
        HeaderNav,
        HeaderNavItem,
        HeaderNavMenu,
        SideNav,
        SideNavItems,
        SideNavMenu,
        SideNavMenuItem,
        SideNavLink,
        SideNavDivider,
        SkipToContent,
        Content,
        Grid,
        Row,
        Column,
    } from "carbon-components-svelte";
    import {Button} from 'carbon-components-svelte'
    import TextBold from 'carbon-icons-svelte/lib/TextBold.svelte'
    import Paragraph from 'carbon-icons-svelte/lib/Paragraph.svelte'
    import Undo from 'carbon-icons-svelte/lib/Undo.svelte'
    import Redo from 'carbon-icons-svelte/lib/Redo.svelte'

    export let editor;
    

    let isSideNavOpen = true;
    </script>

    <Header company="" platformName="Carbeditor"  bind:isSideNavOpen>
        {#if editor}
            <div class="buttons">
                <Button
                    isSelected = {editor.isActive('bold')}
                    kind="ghost"
                    iconDescription = "Bold"
                    icon = {TextBold}
                    on:click={() => editor.chain().focus().toggleBold().run()}
                ></Button>
                <Button
                    isSelected= {editor.isActive('paragraph')}
                    kind = "ghost"
                    iconDescription = "Paragraph"
                    icon = {Paragraph}
                    on:click= {() => editor.chain().focus().setParagraph().run()}
                ></Button>
                <Button
                    kind = "ghost"
                    iconDescription = "Undo"
                    icon = {Undo}
                    isSelected={editor.can().undo()}
                    on:click={()=> editor.chain().focus().undo().run()}
                ></Button> 
                <Button
                    kind = "ghost"
                    iconDescription = "Redo"
                    icon = {Redo}
                    isSelected={editor.can().redo()}
                    on:click={()=> editor.chain().focus().redo().run()}
                ></Button> 
            </div>
        {/if}
    </Header>

<Content>
    <Grid>
        <Row>
        <Column aspectRatio="2x1">
            <slot></slot>
        </Column>
        </Row>
    </Grid>
</Content>

<style>
    .buttons {
        margin-left: auto;
        margin-right: auto;
    }
</style>