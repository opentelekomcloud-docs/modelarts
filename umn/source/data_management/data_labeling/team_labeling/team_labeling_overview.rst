:original_name: datalabel-modelarts_0023.html

.. _datalabel-modelarts_0023:

Team Labeling Overview
======================

Generally, a small data labeling job can be completed by an individual. However, team work is required to label a large dataset. ModelArts provides team labeling, allowing a labeling team that consists of multiple members to manage labels of a dataset.

.. note::

   Team labeling is available only to datasets for image classification, object detection, text classification, named entity recognition, text triplet, and speech paragraph labeling.

For labeling jobs with team labeling enabled, you can create team labeling jobs and assign them to different teams so that team members can complete the labeling jobs together. During data labeling, members can initiate acceptance, continue acceptance, and view acceptance reports.

Team labeling is managed in a unit of teams. To enable team labeling for a dataset, a team must be specified. Multiple members can be added to a team.

-  An account can have a maximum of 10 teams.
-  An account must have at least one team to enable team labeling for datasets. If the account has no team, add a team by referring to :ref:`Adding a Team <en-us_topic_0000002374851721__en-us_topic_0000001139944462_en-us_topic_0186456617_section165361815383>`.
