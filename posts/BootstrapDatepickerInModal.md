---
title: How to solve bootstrap datepicker in modal
published: true
description: Simply wrap your datepicker code in bootstrap's modal shown event.
tags: 'datepicker, modal'
cover_image: ./assets/BootstrapDatepickerInModal/modal-datetime-picker.png
canonical_url: 'https://muathye.com/en/articles/add-bootstrap-datepicker-in-modal.html'
id: 1364434
date: '2023-02-13T21:57:08Z'
---

# How to solve bootstrap datepicker in modal

Simply wrap your datepicker code in bootstrap's modal shown event.

```js
$('#your-modal').on('shown.bs.modal', function() {
  $('.your-date-input').datepicker({});
});
```

::: tip
Here is an full example [Bootstrap DatePicker in Modal](https://codepen.io/muathye/pen/gOjadpa)
:::

```html
<link href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" rel="stylesheet"/>
<script src="//code.jquery.com/jquery-1.11.0.min.js"></script>
<script src="//netdna.bootstrapcdn.com/bootstrap/3.1.1/js/bootstrap.min.js"></script>
<script src="//cdnjs.cloudflare.com/ajax/libs/bootstrap-datepicker/1.3.0/js/bootstrap-datepicker.js"></script>

<style>
    /* Optional: has to be larger than 1050 */
    .datepicker {
      z-index: 1600 !important;
    }
    /* Optional: in case your body is less than datapicker height */
    .modal-body {
        height: 200px;
    }
</style>

<div class="well">
  <button type="button" id="add">Add</button>
</div>
<div id="myModal" class="modal">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h4></h4>
      </div>
      <div class="modal-body">
      </div>
    </div>
  </div>
</div>
```

```javascript
$('#myModal').on('shown.bs.modal', function() {
  $('.input-group.date').datepicker({
    format: "dd/mm/yyyy",
    startDate: "01-01-2015",
    endDate: "01-01-2020",
    todayBtn: "linked",
    autoclose: true,
    todayHighlight: true,
    container: '#myModal modal-body'
  });
});

$("[id=add]").click(function() {
  $("#myModal .modal-header h4").html("Request for Change");
  $("#myModal .modal-body").html('<form class="form-horizontal" role="form"><br /><br /><label class="col-sm-2 control-label">Date Required</label><div class="col-sm-3"><div class="input-group date col-sm-8"><input type="text" class="form-control" id="DateRequired"><span class="input-group-addon"><i class="glyphicon glyphicon-th"></i></span></div></div></form>');
  $("#myModal").modal("show");
});
```
