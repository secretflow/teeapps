# Copyright 2023 Ant Group Co., Ltd.
# 
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
# 
#   http://www.apache.org/licenses/LICENSE-2.0
# 
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM secretflow/trustflow-dev-ubuntu22.04:latest as builder

WORKDIR /home/admin/dev

COPY .bazelrc .bazelversion BUILD.bazel WORKSPACE ./
COPY teeapps ./teeapps
COPY integration_test ./integration_test
COPY bazel ./bazel
COPY scripts/build_sim.sh ./scripts/build_sim.sh

RUN bash ./scripts/build_sim.sh


FROM ubuntu:22.04

ARG config_templates=""
LABEL kuscia.secretflow.config-templates=$config_templates

ARG deploy_templates=""
LABEL kuscia.secretflow.deploy-templates=$deploy_templates

ARG comp_list=""
LABEL kuscia.secretflow.comp_list=$comp_list

ARG translation=""
LABEL kuscia.secretflow.translation=$translation

COPY --from=builder /home/teeapp/sim/teeapps /home/teeapp/sim/teeapps
COPY --from=builder /home/teeapp/python /home/teeapp/python
COPY --from=builder /host/certs /host/certs
COPY --from=builder /host/integration_test /host/integration_test
COPY --from=builder /host/testdata /host/testdata

ENV PATH /home/teeapp/python/bin:$PATH

WORKDIR /home/teeapp/sim/teeapps


