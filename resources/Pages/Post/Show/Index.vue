<template>
    <Layout title="게시글 상세">
        <div>
            <div class="px-4 sm:px-0 flex justify-between">
                <h3 class="text-base font-semibold leading-7 text-gray-900">{{ data.title }}</h3>
                <div class="flex gap-2">
                    <Button title="수정" @event="editPostPage({id: data.id})"/>
                    <Button title="삭제" @event="destroyPost({id: data.id})"/>
                </div>
            </div>
            <div class="mt-6 border-t border-gray-100">
                <dl class="divide-y divide-gray-100">
                    <div class="px-4 py-6 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                        <dt class="text-sm font-medium leading-6 text-gray-900">작성자</dt>
                        <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ data.writer }}</dd>
                    </div>
                    <div class="px-4 py-6 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                        <dt class="text-sm font-medium leading-6 text-gray-900">작성일</dt>
                        <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ getLongTime(data.created_at) }}</dd>
                    </div>
                    <div class="px-4 py-6 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                        <dt class="text-sm font-medium leading-6 text-gray-900">내용</dt>
                        <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ data.content }}</dd>
                    </div>
                </dl>
            </div>
        </div>
        <Modal ref="modalRef"/>
    </Layout>
</template>
<script setup>
import Layout from "../../../Components/Layout.vue";
import useUtils from "../../../js/libs/useUtils.js";
import Button from "../../../Components/Button.vue";
import { ref } from "vue";
import usePost from "../../../js/libs/controller/usePost.js";
import Modal from "../../../Components/Modal.vue";

const props = defineProps(
    {
        data: Object
    }
)

const modalRef = ref(null);

const {editPostPage, destroyPost} = usePost({modalRef})

const { getLongTime } = useUtils();

</script>
