# Terraform Distro Image Provider

This [Terraform](http://terraform.io) provider is for dynamically finding distro images for a given IaaS.

## Status

Development/Testing

Currently only supports ami and gce for coreos and ubuntu.

## Install - Build

```
go get
go build
go install
```

## With Homebrew

```
$ brew tap 'samsung-cnct/terraform-provider-coreosbox'
$ brew install terraform-provider-coreosbox
```

## Usage


```
resource "distro_distro_coreos_ami" "current_ami" {
  channel = "alpha"
  virtualization = "hvm"
  region = "us-east-1"
  version = "current"
}

resource "distro_coreos_ami" "versioned_ami" {
  channel = "stable"
  virtualization = "hvm"
  region = "us-east-1"
  version = "647.2.0"
}

resource "distro_coreos_gce" "current_gce" {
  channel = "alpha"
  version = "current"
}

resource "distro_coreos_gce" "versioned_gce" {
  channel = "stable"
  version = "647.2.0"
}

resource "distro_coreos_vagrant" "current_vagrant" {
  channel = "alpha"
  version = "current"
  hypervisor = "virtualbox"
}

resource "distro_coreos_vagrant" "versioned_vagrant" {
  channel = "stable"
  version = "647.2.0"
  hypervisor = "virtualbox"
}

resource "distro_coreos_vagrant" "current_vagrant_vmware" {
  channel = "alpha"
  version = "current"
  hypervisor = "vmware"
}

resource "distro_coreos_vagrant" "versioned_vagrant_vmware" {
  channel = "stable"
  version = "647.2.0"
  hypervisor = "vmware"
}

output "info_ami" {
    value = "Version: ${distro_coreos_ami.current_ami.version_out}, ami: ${distro_coreos_ami.current_ami.box_string}." 
}

output "info_ami_versioned" {
    value = "Version: ${distro_coreos_ami.versioned_ami.version_out}, ami: ${distro_coreos_ami.versioned_ami.box_string}." 
}

output "info_gce" {
    value = "Version: ${distro_coreos_gce.current_gce.version_out}, box: ${distro_coreos_gce.current_gce.box_string}." 
}

output "info_gce_versioned" {
    value = "Version: ${distro_coreos_gce.versioned_gce.version_out}, box: ${distro_coreos_gce.versioned_gce.box_string}." 
}

output "info_vagrant" {
    value = "Version: ${distro_coreos_vagrant.current_vagrant.version_out}, box: ${distro_coreos_vagrant.current_vagrant.box_string}." 
}

output "info_vagrant_versioned" {
    value = "Version: ${distro_coreos_vagrant.versioned_vagrant.version_out}, box: ${distro_coreos_vagrant.versioned_vagrant.box_string}." 
}

output "info_vmware" {
    value = "Version: ${distro_coreos_vagrant.current_vagrant_vmware.version_out}, box: ${distro_coreos_vagrant.current_vagrant_vmware.box_string}." 
}

output "info_vmware_versioned" {
    value = "Version: ${distro_coreos_vagrant.versioned_vagrant_vmware.version_out}, box: ${distro_coreos_vagrant.versioned_vagrant_vmware.box_string}." 
}
```
