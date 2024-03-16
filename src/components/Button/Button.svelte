<script lang="ts">
    import styles from './button.module.scss';
    import classNames from "classnames";

    type Variant = 'solid' | 'light' | 'outline' | 'flat' | 'ghost' | 'glow';
    type Color = 'primary'

    export const variant: Variant = 'solid';
    export const color: Color = 'primary';
    export const darkMode = false;
    export const disabled = false;

    const mainClass = styles[`button-${variant}-${color}`];

    let classList = '';

    $: classList = classNames(
        $$props.class,
        mainClass,
        {
            [styles['button-disabled']]: disabled
        },
        {
            [styles['dark-mode']]: darkMode
        },

    )
</script>

<button
        {...$$restProps}
        class={classList}
        disabled={disabled}
>
    <slot/>
</button>