# Feature decisions

Implemented in this release: clearer homepage value proposition and target audience wording; preset templates for PPPoE, Hotspot, and NAT/Firewall generators; stronger address-pool validation; pre-import testing guidance; RouterOS v6/v7 compatibility notes; WAN context warnings; social metadata; safer SEO copy; and repaired article/script closures. Presets only prefill editable example values and do not replace topology review.

Deliberately not implemented as one-click configuration: a combined WAN DHCP/Static/PPPoE generator, generic VLAN topology, or automatic full CGNAT scripts. These depend on topology-specific decisions such as bridge/trunk/access design, routing, public/shared address pools, logging, and remote-management safeguards. They should be separate documented tools with their own test cases rather than unsafe checkboxes in an existing generator.

The RouterOS selector changes review notes and does not guarantee feature-level compatibility. Always validate output against the exact device, RouterOS release, addressing plan, RADIUS platform, and firewall policy before import.
