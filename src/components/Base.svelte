<!-- Base.svelte -->
<script context="module">
    export function baseGet() {
        const data = localStorage.getItem("MYFLIX");
        return JSON.parse(data) || false;
    }

    export function baseSet(value) {
        localStorage.setItem("MYFLIX", JSON.stringify(value));
    }

    export function baseAddMedia(data) {
        const BD = baseGet();
        const id = Object.keys(BD.mediaList).length;
        data.id = id;
        BD.mediaList[id] = data;
        baseSet(BD);
    }

    export function baseUpdateMedia(id, field, value) {
        const BD = baseGet();
        if (BD.mediaList[id]) {
            BD.mediaList[id][field] = value;
            baseSet(BD);
        }
    }
    
    export function baseRemoveMedia(id) {
        const mediaList = baseGet().mediaList;
        delete mediaList[id];
        baseSet({ ...baseGet(), mediaList });
    }

    export function baseGetMediaList() {
        const mediaList = baseGet().mediaList;
        return Object.values(mediaList);
    }

    if (!localStorage.getItem("MYFLIX")) {
        baseSet({ config: { lang: "en", background: "black" }, mediaList: {} });
    }
</script>
