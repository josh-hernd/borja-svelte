<script lang="ts">
    export let open: boolean;
    </script>
    <button
        class:open
        on:click={() => (open = !open)}
        style="transition: color {$$props.duration}s ease-in-out; color: {$$props.open ? $$props.menuColor : $$props.burgerColor};"
    >
        <svg width="32" height="32">
            <line
                id="top"
                x1="0"
                y1="9"
                x2="32"
                y2="9"
                style="transition: transform {$$props.duration}s ease-in-out, opacity {$$props.duration}s ease-in-out;"
            />
            <line
                id="mid"
                x1="0"
                y1="18.5"
                x2="32"
                y2="18.5"
                style="transition: transform {$$props.duration}s ease-in-out, opacity {$$props.duration}s ease-in-out;"
            />
            <line
                id="bot"
                x1="0"
                y1="28"
                x2="32"
                y2="28"
                style="transition: transform {$$props.duration}s ease-in-out, opacity {$$props.duration}s ease-in-out;"
            />
        </svg>
    </button>
    
    <style lang="sass">
        button 
            position: relative
            margin: 0px
            padding: 0px
            display: flex
            align-items: center
            justify-content: center
            z-index: 10
            background-color: Transparent
            background-repeat: no-repeat
            border: none
            cursor: pointer
            overflow: hidden
            outline: none
        
        svg line 
            stroke: currentColor
            stroke-width: 3
        
        /* rotate the top line */
        .open #top 
            transform: translate(10px, 0px) rotate(45deg)
        
        /* hide the middle */
        .open #mid 
            opacity: 0
        
        /* rotate the bottom line */
        .open #bot 
            transform: translate(-15px, 8px) rotate(-45deg)
        
    </style>