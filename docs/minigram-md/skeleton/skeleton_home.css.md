# skeleton/skeleton_home.css

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `skeleton/skeleton_home.css` |
| Extension | `.css` |
| Bytes | 6456 |
| Lines | 301 |
| SHA-256 | `9545117b6fb470842fa2c8832357ebde4a32974960cfed5c5b310ff5b4b06a5b` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`skeleton`

The local intelligence engine detected
0 direct dependencies
and 0 consumers.

## 5. Dependencies

- None

## 6. Used By

- None

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- None

## 9. Exports

- None

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- No detected errors

## 12. Project Systems

- None

## 13. Project Risks

- None

## 14. Recommendations

- None

## 15. Execution / Architecture Flow

See the generated relation graph and file-level flows.

---

# ORIGINAL SOURCE CODE

The following is the **exact local source content**
read from:

`/storage/emulated/0/MINIGRAM1/skeleton/skeleton_home.css`

It is NOT AI generated or rewritten.

```css
/* =========================================================
   MINIGRAM — HOME SKELETON
   Owner: index.html
   Path: skeleton/skeleton_home.css

   IMPORTANT:
   - No JS required
   - No external dependency
   - Designed for instant first paint
   - Home skeleton only
========================================================= */


/* =========================================================
   HOME SKELETON ROOT
========================================================= */

#mainContent[data-skeleton-page="home"] {
    width: 100%;
    min-height: 100vh;
    background: #000;
    color: transparent;
    overflow: hidden;
}


/* =========================================================
   SKELETON COMMON
========================================================= */

#mainContent[data-skeleton-page="home"] .skel {
    background: #171717;
    border-radius: 8px;
}


/* =========================================================
   STORIES
========================================================= */

#mainContent[data-skeleton-page="home"] .skeleton-stories {
    display: flex;
    gap: 13px;

    width: 100%;
    padding: 12px 14px;

    overflow: hidden;

    border-bottom: 1px solid rgba(255,255,255,.07);
}


#mainContent[data-skeleton-page="home"] .skeleton-story {
    flex: 0 0 64px;

    width: 64px;
    height: 64px;

    border-radius: 50%;

    background: #171717;
}


/* =========================================================
   POST
========================================================= */

#mainContent[data-skeleton-page="home"] .skeleton-post {
    width: 100%;

    border-bottom: 1px solid rgba(255,255,255,.07);
}


/* =========================================================
   POST HEADER
========================================================= */

#mainContent[data-skeleton-page="home"] .skeleton-user {
    display: flex;
    align-items: center;
    gap: 10px;

    width: 100%;
    height: 58px;

    padding: 10px 13px;
}


#mainContent[data-skeleton-page="home"] .skeleton-avatar {
    flex: 0 0 36px;

    width: 36px;
    height: 36px;

    border-radius: 50%;

    background: #171717;
}


#mainContent[data-skeleton-page="home"] .skeleton-user-info {
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 7px;

    flex: 1;
}


#mainContent[data-skeleton-page="home"] .skeleton-name {
    width: 90px;
    height: 10px;

    border-radius: 5px;

    background: #171717;
}


#mainContent[data-skeleton-page="home"] .skeleton-subtitle {
    width: 55px;
    height: 7px;

    border-radius: 4px;

    background: #111;
}


/* =========================================================
   MORE BUTTON
========================================================= */

#mainContent[data-skeleton-page="home"] .skeleton-more {
    width: 28px;
    height: 28px;

    border-radius: 50%;

    background: #111;
}


/* =========================================================
   POST MEDIA
========================================================= */

#mainContent[data-skeleton-page="home"] .skeleton-media {
    width: 100%;

    aspect-ratio: 1 / 1;

    background: #111;
}


/* =========================================================
   ACTION BAR
========================================================= */

#mainContent[data-skeleton-page="home"] .skeleton-actions {
    display: flex;
    align-items: center;
    gap: 14px;

    width: 100%;
    height: 48px;

    padding: 8px 13px;
}


#mainContent[data-skeleton-page="home"] .skeleton-action {
    width: 23px;
    height: 23px;

    border-radius: 50%;

    background: #171717;
}


#mainContent[data-skeleton-page="home"] .skeleton-action-right {
    margin-left: auto;
}


/* =========================================================
   CAPTION
========================================================= */

#mainContent[data-skeleton-page="home"] .skeleton-caption {
    width: 100%;
    padding: 0 13px 14px;
}


#mainContent[data-skeleton-page="home"] .skeleton-line {
    height: 8px;

    margin-bottom: 7px;

    border-radius: 4px;

    background: #171717;
}


#mainContent[data-skeleton-page="home"] .skeleton-line.long {
    width: 72%;
}


#mainContent[data-skeleton-page="home"] .skeleton-line.medium {
    width: 48%;
}


#mainContent[data-skeleton-page="home"] .skeleton-line.short {
    width: 28%;
}


/* =========================================================
   VERY LIGHT SHIMMER
========================================================= */

@media (prefers-reduced-motion: no-preference) {

    #mainContent[data-skeleton-page="home"] .skel,
    #mainContent[data-skeleton-page="home"] .skeleton-story,
    #mainContent[data-skeleton-page="home"] .skeleton-avatar,
    #mainContent[data-skeleton-page="home"] .skeleton-name,
    #mainContent[data-skeleton-page="home"] .skeleton-subtitle,
    #mainContent[data-skeleton-page="home"] .skeleton-more,
    #mainContent[data-skeleton-page="home"] .skeleton-media,
    #mainContent[data-skeleton-page="home"] .skeleton-action,
    #mainContent[data-skeleton-page="home"] .skeleton-line {

        animation:
            minigramHomeSkeletonPulse
            1.2s
            ease-in-out
            infinite
            alternate;
    }

}


@keyframes minigramHomeSkeletonPulse {

    from {
        opacity: .72;
    }

    to {
        opacity: 1;
    }

}


/* =========================================================
   LOW-END DEVICE
   Disable animation for cheaper rendering
========================================================= */

@media (prefers-reduced-motion: reduce) {

    #mainContent[data-skeleton-page="home"] * {
        animation: none !important;
    }

}


/* =========================================================
   SAFE MOBILE WIDTH
========================================================= */

@media (max-width: 480px) {

    #mainContent[data-skeleton-page="home"] .skeleton-stories {
        gap: 12px;
        padding-left: 12px;
        padding-right: 12px;
    }

    #mainContent[data-skeleton-page="home"] .skeleton-story {
        width: 62px;
        height: 62px;
        flex-basis: 62px;
    }

}
```

---

Generated by MiniGram MD Intelligence V6.
