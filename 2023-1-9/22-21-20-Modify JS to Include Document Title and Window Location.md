## USER
Can you modify the javascript below so that it also includes document.title and window.location.href in the json files. Return the rewritten solution and don't say anything else.

!function () {
    for (var e = {meta: {timestamp: new Date(new Date(new Date(new Date).toISOString()).getTime() - 6e4 * (new Date).getTimezoneOffset()).toISOString().slice(0, 19).replace("T", " ")}}, t = [], n = document.querySelectorAll("[class*='min-h-[20px]']"), a = 0; a < n.length; a++) {
        var o = {index: a}, s = [], l = n[a].firstChild;
        if (l) {
            if (l.nodeType === Node.ELEMENT_NODE) {
                var d = l.childNodes;
                l.className.includes("request-") && (o.type = "response");
                for (var i = 0; i < d.length; i++) {
                    var c, p, r = d[i];
                    r.nodeType === Node.ELEMENT_NODE && (c = r.tagName, p = r.textContent, "P" === c && s.push({
                        type: "p",
                        data: p
                    }), "OL" !== c && "UL" !== c || (listItems = [], r.childNodes.forEach((e, t) => {
                        e.nodeType === Node.ELEMENT_NODE && "LI" === e.tagName && listItems.push({
                            type: "li",
                            data: e.textContent
                        })
                    }), "OL" === c && s.push({type: "ol", data: listItems}), "UL" === c && s.push({
                        type: "ul",
                        data: listItems
                    })), "PRE" === c) && s.push({type: "pre", data: p})
                }
            }
            l.nodeType === Node.TEXT_NODE && (o.type = "prompt", s.push(l.textContent)), o.message = s, t.push(o)
        }
    }

    e.chats = t, console.save = function (e, t) {
        t = t || "chatgpt.json", "object" == typeof e && (e = JSON.stringify(e, void 0, 4));
        var e = new Blob([e], {type: "text/json"}), n = document.createElement("a"),
            t = (n.download = t, n.href = window.URL.createObjectURL(e), n.dataset.downloadurl = ["text/json", n.download, n.href].join(":"), new MouseEvent("click", {
                canBubble: !0,
                cancelable: !1,
                view: window,
                detail: 0,
                screenX: 0,
                screenY: 0,
                clientX: 0,
                clientY: 0,
                ctrlKey: !1,
                altKey: !1,
                shiftKey: !1,
                metaKey: !1,
                button: 0,
                relatedTarget: null
            }));
        n.dispatchEvent(t)
    }, console.save(e, "chatgpt.json")
}();

## ASSISTANT
!function () {
    for (var e = {meta: {timestamp: new Date(new Date(new Date(new Date).toISOString()).getTime() - 6e4 * (new Date).getTimezoneOffset()).toISOString().slice(0, 19).replace("T", " "), document_title: document.title, window_location: window.location.href}}, t = [], n = document.querySelectorAll("[class*='min-h-[20px]']"), a = 0; a < n.length; a++) {
        var o = {index: a}, s = [], l = n[a].firstChild;
        if (l) {
            if (l.nodeType === Node.ELEMENT_NODE) {
                var d = l.childNodes;
                l.className.includes("request-") && (o.type = "response");
                for (var i = 0; i < d.length; i++) {
                    var c, p, r = d[i];
                    r.nodeType === Node.ELEMENT_NODE && (c = r.tagName, p = r.textContent, "P" === c && s.push({
                        type: "p",
                        data: p
                    }), "OL" !== c && "UL" !== c || (listItems = [], r.childNodes.forEach((e, t) => {
                        e.nodeType === Node.ELEMENT_NODE && "LI" === e.tagName && listItems.push({
                            type: "li",
                            data: e.textContent
                        })
                    }), "OL" === c && s.push({type: "ol", data: listItems}), "UL" === c && s.push({
                        type: "ul",
                        data: listItems
                    })), "PRE" === c) && s.push({type: "pre", data: p})
                }
            }
            l.nodeType === Node.TEXT_NODE && (o.type = "prompt", s.push(l.textContent)), o.message = s, t.push(o)
        }
    }

    e.chats = t, console.save = function (e, t) {
        t = t || "chatgpt.json", "object" == typeof e && (e = JSON.stringify(e, void 0, 4));
        var e = new Blob([e], {type: "text/json"}), n = document.createElement("a"),
            t = (n.download = t, n.href = window.URL.createObjectURL(e), n.dataset.downloadurl = ["text/json", n.download, n.href].join(":"), new MouseEvent("click", {
                canBubble: !0,
                cancelable: !1,
                view: window,
                detail: 0,
                screenX: 0,
                screenY: 0,
                clientX: 0,
                clientY: 0,
                ctrlKey: !1,
                altKey: !1,
                shiftKey: !1,
                metaKey: !1,
                button: 0,
                relatedTarget: null
            }));
        n.dispatchEvent