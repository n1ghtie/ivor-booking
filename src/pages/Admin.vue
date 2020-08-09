<template>
    <div class="admin">
        <div class="sidebar">
            <div class="sidebar-menu">
                <p class="sidebar-label">
                    Admin Menu
                </p>

                <ul>
                    <li>
                        <router-link to="/admin">Bookings</router-link>
                    </li>
                    <li>
                        <router-link to="/admin/services">Services</router-link>
                    </li>
                </ul>
            </div>
        </div>

        <div class="content">
            <h1>Recent Bookings</h1>
            <table>
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Email</th>
                        <th>Phone Number</th>
                        <th>Service</th>
                        <th>Booking Date</th>
                        <th>Status</th>
                        <th>Actions</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Andrejs Gubars</td>
                        <td>andrejs@email.com</td>
                        <td>07447 123211</td>
                        <td>Fade</td>
                        <td>12 August 2020 10:20</td>
                        <td>Needs approval</td>
                        <td>
                            <button class="button is-success">Approve</button>
                            {{' '}}
                            <button class="button is-danger">Cancel</button>
                        </td>
                    </tr>

                    <tr>
                        <td>Ivan Ivanov</td>
                        <td>ivan@email.com</td>
                        <td>07447 123211</td>
                        <td>Normal Haircut</td>
                        <td>12 August 2020 11:20</td>
                        <td>Needs approval</td>
                        <td>
                            <button class="button is-success">Approve</button>
                            {{' '}}
                            <button class="button is-danger">Cancel</button>
                        </td>
                    </tr>

                    <tr>
                        <td>Arman Arojan</td>
                        <td>arman@email.com</td>
                        <td>07447 123211</td>
                        <td>Normal Haircut</td>
                        <td>12 August 2020 13:20</td>
                        <td>Approved</td>
                        <td>
                        </td>
                    </tr>

                    <tr>
                        <td>Dima Ivanov</td>
                        <td>dima@email.com</td>
                        <td>07447 123211</td>
                        <td>Fade</td>
                        <td>12 August 2020 12:20</td>
                        <td>Needs approval</td>
                        <td>
                            <button class="button is-success">Approve</button>
                            {{' '}}
                            <button class="button is-danger">Cancel</button>
                        </td>
                    </tr>

                    
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Admin'
}
</script>

<style lang="scss">
.admin {
    display: flex;
}

.content {
    padding: 20px;
    width: 100%;
}
.sidebar {
    display: flex;
    flex-direction: column;
    flex-shrink: 0;
    width: 16rem;
    padding: 3rem 1rem;
    background: #f5f5f5;
    height: 100vh;
}
.sidebar-label {
    margin-bottom: .5em;
    color: #7a7a7a;
    font-size: .9em;
    text-transform: uppercase;
    letter-spacing: .1em;
}
</style>