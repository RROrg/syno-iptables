SPK_NAME = rr-iptables
SPK_VERS = 1.0
SPK_REV = 1
SPK_ICON = src/rr.png

DEPENDS = 

REQUIRE_KERNEL ?= 1
REQUIRE_KERNEL_MODULE  =

REQUIRE_KERNEL_MODULE += CONFIG_NETFILTER:net/netfilter:netfilter
# net/netfilter
ifeq ($(call version_lt, $(TC_KERNEL), 4.4),1)
REQUIRE_KERNEL_MODULE += CONFIG_NETFILTER_TPROXY:net/netfilter:nf_tproxy_core  # only 3.x
endif
REQUIRE_KERNEL_MODULE += CONFIG_NETFILTER_XT_MARK:net/netfilter:xt_mark
REQUIRE_KERNEL_MODULE += CONFIG_NETFILTER_XT_SET:net/netfilter:xt_set
REQUIRE_KERNEL_MODULE += CONFIG_NETFILTER_XT_NAT:net/netfilter:xt_nat
REQUIRE_KERNEL_MODULE += CONFIG_NETFILTER_XT_CONNMARK:net/netfilter:xt_connmark
REQUIRE_KERNEL_MODULE += CONFIG_NETFILTER_XT_MATCH_COMMENT:net/netfilter:xt_comment
REQUIRE_KERNEL_MODULE += CONFIG_NETFILTER_XT_MATCH_SOCKET:net/netfilter:xt_socket
REQUIRE_KERNEL_MODULE += CONFIG_NETFILTER_XT_MATCH_STRING:net/netfilter:xt_string
REQUIRE_KERNEL_MODULE += CONFIG_NETFILTER_XT_TARGET_TPROXY:net/netfilter:xt_TPROXY
REQUIRE_KERNEL_MODULE += CONFIG_NETFILTER_XT_MATCH_OWNER:net/netfilter:xt_owner
# net/netfilter/ipset
REQUIRE_KERNEL_MODULE += CONFIG_IP_SET:net/netfilter/ipset:ip_set
REQUIRE_KERNEL_MODULE += CONFIG_IP_SET_HASH_IP:net/netfilter/ipset:ip_set_hash_ip
REQUIRE_KERNEL_MODULE += CONFIG_IP_SET_HASH_NET:net/netfilter/ipset:ip_set_hash_net
# net/ipv4/netfilter
REQUIRE_KERNEL_MODULE += CONFIG_IP_NF_MANGLE:net/ipv4/netfilter:iptable_mangle
# net/ipv6/netfilter
ifeq ($(call version_ge, $(TC_KERNEL), 4.4),1)
REQUIRE_KERNEL_MODULE += CONFIG_IP6_NF_NAT:net/ipv6/netfilter:ip6table_nat
endif
REQUIRE_KERNEL_MODULE += CONFIG_IP6_NF_RAW:net/ipv6/netfilter:ip6table_raw
REQUIRE_KERNEL_MODULE += CONFIG_IP6_NF_MANGLE:net/ipv6/netfilter:ip6table_mangle
REQUIRE_KERNEL_MODULE += CONFIG_IP6_NF_TARGET_MASQUERADE:net/ipv6/netfilter:ip6t_MASQUERADE
REQUIRE_KERNEL_MODULE += CONFIG_NF_NAT_IPV6:net/ipv6/netfilter:nf_nat_ipv6
REQUIRE_KERNEL_MODULE += CONFIG_NF_NAT_MASQUERADE_IPV6:net/ipv6/netfilter:nf_nat_masquerade_ipv6
# lib
REQUIRE_KERNEL_MODULE += CONFIG_TEXTSEARCH:lib:textsearch
REQUIRE_KERNEL_MODULE += CONFIG_TEXTSEARCH_BM:lib:ts_bm


MAINTAINER = RROrg
DESCRIPTION = "iptables"
CHANGELOG = "1. Support DSM-7.0, DSM-7.1 and DSM-7.2"


STARTABLE = no
DISPLAY_NAME = SynoKernel iptables drivers

HOMEPAGE = https://www.kernel.org/
LICENSE  = GPLv2

SPK_DEPENDS = synocli-kernel

STRIP_TARGET = nop
POST_STRIP_TARGET = synokernel-iptables-install

ADDITIONAL_CXXFLAGS += -D__DECOMPRESSION_TYPE__=304403268

include ../../mk/spksrc.spk.mk

.PHONY: synokernel-iptables-install
synokernel-iptables-install:
	# Install iptables modules
