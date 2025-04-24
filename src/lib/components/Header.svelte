<header>
    <h1>Aim</h1>

    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/" class="hidden">Training</a></li>
        <li><a href="/" class="hidden">Leaderboard</a></li>
        <li><a href="/about">About</a></li>
    </ul>
</header>

<style>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem;
        background: var(--button-background);
        border-bottom: 1px solid var(--blue-primary-color);
        flex-wrap: wrap;
    }

    h1 {
        cursor: pointer;
        color: var(--blue-secondary-color);
        transition: color 0.3s ease-in-out;
    }
    
    h1:hover {
        color: var(--blue-primary-color);
        text-decoration: underline;
    }

    ul {
        list-style: none;
        display: flex;
        flex-direction: row;
        gap: 1rem;
    }

    a {
        color: var(--text-color);
        text-decoration: none;
        transition: color 0.3s ease-in-out;
    }

    a:hover {
        color: var(--title-color);
        text-decoration: underline;
    }

    @media (max-width: 600px) {
        .hidden {
            display: none;
        }
    }
</style>